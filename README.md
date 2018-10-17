### DeviceDetector
---
.rb
https://github.com/podigee/device_detector

.php
https://github.com/matomo-org/device-detector

```
gem 'devise_detector'
bundle
gem install device_detector

```

```ruby
user_agent = 'Mozilla/5.0 (Windows NT 6.2; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/30.0.1599.17 Safari/537.36'
client = DeviceDetector.new(user_agent)
client.name
client.full_version
client.os_name
client.os_full_version
client.device_name
client.device_type

client.known?

DeviceDetector.configure do |config|
  config.max_cache_keys = 5_000
end

require 'device_detector'
require 'browser'
require 'user_agent'
require 'benchmark'
user_agent_strings = File.read('./tmp/user_agent_strings.txt').split("\n")
Benchmark.bm(15) do |x|
  x.report('device_detector'){
    user_agent_strings.each { |uas| DeviceDetector.new(uas).name }
  }
  x.report('browser'){
    user_agent_strings.each { |uas| Browser.new(ua: uas).name }
  }
  x.report('useragent'){
    user_agent_strings.each { |uas| UserAgent.parse(uas).browser }
  }
end

```

```

```





