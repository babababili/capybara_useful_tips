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

# fill the input /select box by label

    fill_in('Domain', with: 'www.google.com')
    select 'SGD', from: 'Currency'

# missing api(v.useful)
http://makandracards.com/makandra/1422-capybara-the-missing-api

# Understanding ruby yield, passing parameter to method
https://www.codecademy.com/forum_questions/52bc1930631fe91466001658
```
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
```


# Check the parent element and find options
```find_field('Catalog').find(:xpath, '..').find('option[value="10"]')```

``` within find_field('Catalog').find(:xpath, '..') do
        find('option[value="10"]').click
    end
```


[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/babababili/capybara_useful_tips/trend.png)](https://bitdeli.com/free "Bitdeli Badge")

