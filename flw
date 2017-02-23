#!/usr/bin/env lua

local ml = require("ml")

-- lost focus history
local focus = {}

local function filter(table, pred)
    local out = {}
    local i = 1
    for k, v in ipairs(table) do
        if pred(k, v) then
            out[i] = v
            i = i + 1
        end
    end
    return out
end

while true do
    local input = io.read()

    -- loop until ^D
    if input == nil then
        break
    end

    -- wew emits events as type:wid
    local pair = ml.split(input, ":")

    -- split them up
    local event = tonumber(pair[1])
    local wid = pair[2]

    if event == 10 then
        -- window lost focus
        focus = filter(focus, function(k, v)
            return v ~= wid
        end)

        table.insert(focus, wid)
    elseif event == 17 then
        -- window destroyed
        local index = ml.indexof(focus, wid)

        if index ~= nil then
            local remove = focus[index]

            focus = filter(focus, function(k, v)
                return v ~= remove
            end)

            if focus[#focus] ~= nil then
                os.execute("wtf " .. focus[#focus])
            end
        end
    elseif event == nil then
        -- someone's messing around
        print("please start flw with the executable script")
    end
end

