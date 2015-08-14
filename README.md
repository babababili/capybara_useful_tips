# capybara_useful_tips

find('input[name="Sex"][value="M"]') # to find by multiple attributes

find('#zk_comp_197')[:src] #retrieve attribute value

# some buttons does not appear, retry or extend wait times
    12.times do
      find("input.btn.full.loginBtn").click
      puts 'me'
      login_success_check = find_button('Pay Now') rescue nil
      break unless login_success_check.nil?
    end

or
    using_wait_time(10) do
      find("input.btn.full.loginBtn").click
    end

# fill in option with the first choice
find('select[name="comboboxInstallments"]').find(:xpath, 'option[1]').select_option

# get all options on a select
find('#creditCardPaymentCardTypeSelect').all('option').collect(&:text)
# select option by value
within '#creditCardPaymentForm' do
  find("option[value='UT']").click
end

# find the child element
find('fieldset.cardNumber input')

# Understanding ruby yield, passing parameter to method
  def parameters(val)
    puts 'Here, have two random numbers.'
    yield val if block_given?
    puts 'Now say thank you!'
  end
  it 'sdfdsfds' do
    parameters(rand(10)) { |v| myval(v) }
  end

  def myval(v)
    puts "#{v}" #puts "#{v}, #{x}, #{y}"
  end
