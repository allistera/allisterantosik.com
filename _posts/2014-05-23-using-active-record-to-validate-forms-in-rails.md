---
layout:     post
title:      Using Active Record to Validate Forms in Rails
date:       2014-05-31
summary:    Validating inputted data from forms in Ruby on Rails can be at first be a challenging, there are no central form validation classes like there are in other web frameworks. Although Active Record is primarily used as an interface to a regional database it can be used for non-Database data validation using it's ActiveModel::Validations component. In this example I will be validating posted data (Name, email address and message body) from a contact form.
---

Validating inputted data from forms in Ruby on Rails can be at first be a challenging, there are no central form validation classes like there are in other web frameworks. Although Active Record is primarily used as an interface to a regional database it can be used for non-Database data validation using it's ActiveModel::Validations component. In this example I will be validating posted data (Name, email address and message body) from a contact form.

## Create our Contact Model

To get started, lets begin by creating the contact model that will contain the validation logic, run this command in your terminal:

<code>$ rails generate model Contact --no-test-framework --migration=false</code>

Notice we are telling the generate command not to create any testing or migrations files, only the Contact model will be created in <code>/app/models/contact.rb</code>.


## Write our Models Logic

Open up the newly created contact model in your preferred text editor, rails has generated a basic model class for us to modify. The first issue is that it inherits Active Record::Base, as we are not going to interface with an actual database **remove '< ActiveRecord::Base' from the first line**. We do on the other hand require the Validations, Conversion, and Naming classes, these can be included at the top.

Here is my final Contact Model in full:

**/app/models/contact.rb**

	class Contact
      include ActiveModel::Validations
      include ActiveModel::Conversion
      extend ActiveModel::Naming

      attr_accessible :name, :address, :body

      # Set validation rules
      validates_presence_of :name
      validates_format_of :address, :with => /^[-a-z0-9_+\.]+\@([-a-z0-9]+\.)+[a-z0-9]{2,4}$/i
      validates_length_of :body, :maximum => 500

      def initialize(attributes = {})
        attributes.each do |name, value|
          send("#{name}=", value)
        end
      end

      def persisted?
        false
      end

	end


As you can see from the validation rules we set the following validation rules for each attribute:

+ name - Must be set
+ address - Conforms with the giving regular expression, in this case a valid email address
+ body - Maximum length of 500 characters

I have shown three methods (validates\_presence\_of, validates\_format\_of and validates\_length\_of) other examples include:

+ validates\_acceptance\_of
+ validates\_confirmation\_of
+ validates\_exclusion\_of
+ validates\_inclusion\_of
+ validates\_numericality\_of
+ validates\_size\_of

Details on these can be found on [API Dock](http://apidock.com/rails/ActiveModel/Validations/HelperMethods).

## Using the Model in our Controller

Using the Contact model in the controller is fairly easy, I first created two methods; index and post, the first to display the form and the latter to handle posted data.

	def index
    	@message = Contact.new
    end

	def post
		@message = Contact.new(params[:message])
    	if @message.valid?
        	# Validation Success - Send email logic here
        	flash[:notice] = "Message sent! Thank you for getting in contact, I will get back to you ASAP."
        	redirect_to root_url
      	else
        	flash[:alert] = "There was an error sending your message, please check all fields and send again."
        	redirect_to :action => 'index'
      end
	end


## Using the Model in our View

Once the form has been posted it will validate the inputted values using the rules that we specified in the Contact model, for a full picture this is the view that I am using:

    <% flash.each do |name, msg| %>
      <% if msg.is_a?(String) %>
          <div class="alert alert-<%= name == :notice ? "success" : "error" %>">
              <a class="close" data-dismiss="alert">&#215;</a>
              <%= content_tag :div, msg, :id => "flash_#{name}" %>
          </div>
      <% end %>
    <% end %>

	<%= form_tag('contact/post', :class => 'form-horizontal') do %>

    <div class="control-group">
      <%= label :name, "Name:", :class => 'control-label' %>
      <div class="controls">
          <%= text_field :message, :name, :class => 'span3' %>
      </div>
    </div>

    <div class="control-group">
      <%= label :address, "Email Address:", :class => 'control-label' %>
      <div class="controls">
          <%= email_field :message, :address , :class => 'span3' %>
      </div>
    </div>

    <div class="control-group">
      <%= label :body, "Message:", :class => 'control-label' %>
      <div class="controls">
        <%= text_area :message, :body, :class => "input-block-level", :rows => '10' %>
      </div>
    </div>

    <div class="form-actions">
      <%= submit_tag "Send Message", :class => 'btn btn-primary' %> &nbsp;
      <button type="reset" class="btn">Reset</button>
    </div>

    <% end %>


## Find Out More
+ [Rails Guide - Active Record Validations and Callbacks](http://guides.rubyonrails.org/active_record_validations_callbacks.html)
+ [API Dock - Validation Helper Methods](http://apidock.com/rails/ActiveModel/Validations/HelperMethods)
