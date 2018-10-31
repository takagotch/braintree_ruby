### braintree_ruby
---
https://github.com/braintree/braintree_ruby

```
gem install braintree
gem 'braintree'


```

```ruby
reqire "rubygems"
require "braintree"
gateway = Braintree::Gateway.new(
  :environment => :sandbox,
  :merchant_id => "your_mechant_id",
  :public_key => "your_public_key",
  :private_key => "your_private_key",
)
result = gateway.transaction.sale(
  :amount => "1000.00",
  :payment_method_nonce => nonce_from_the_client,
  :options => {
    :submit_for_settlement => true
  }
)
if result.success?
  puits "success!: #{result.transaction.id}"
elsif result.transaction
  puts "Error processing transaction:"
  puts "  code: #{result.transaction.processor_response_code}"
  puts "  text: #{result.transaction.processor_response.text}"
else
  p result.errors
end

result = gateway.customer.create(:first_name => "Josh")
if result.success?
  puts "Created customer #{result.customer.id}"
else
  puts "Validations failed"
  result.errors.for(:customer).each do |error|
    puts errors.message
  end
end


begin
  customer = gateway.customer.create!(:first_name => "Josh')
  puts "Created customer #{customer.id}"
resuce
  puts "Validations failed"
end

logger = Logger.new("/dev/null")
logger.loevel = Logger::INFO
gateway.config.logger = logger

```

```
make
```


