-- This Lua script increments a counter value stored in Redis by 1
-- If the counter key does not exist, it initializes it with a value of 0

-- Define the Redis key for the counter
local counterKey = "myCounter"

-- Check if the key exists
if redis.call("EXISTS", counterKey) == 0 then
  -- Key does not exist, initialize it with a value of 0
  redis.call("SET", counterKey, 0)
end

-- Increment the counter by 1 and return its new value
return redis.call("INCR", counterKey)
