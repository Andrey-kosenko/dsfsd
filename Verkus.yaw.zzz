client.log("Verkus.yaw", color.new(145, 197, 56), "Verkus.yaw", true)
client.log("", color.new(145, 197, 56), "Verkus.yaw", true)
client.log(" ", color.new(145, 197, 56), "Verkus.yaw", true)
client.log("", color.new(145, 197, 56), "Verkus.yaw", true)
client.log("▒▓███▀▒▒▓█   ▓██▒██▒   ░██▒▒░▒████▒██████▒▒▒░▒████▒██░   ▓██░▒██████▒▒▒░▒██████ ▒██▒ ▒██▒  ░ ██▒▓░▒███████▒", color.new(145, 197, 56), "Verkus.yaw", true)
client.log("░▒   ▒ ░▒▒   ▓▒█░ ▒░   ░  ░░░░ ▒░ ▒ ▒▓▒ ▒ ░░░░ ▒░ ░ ▒░   ▒ ▒ ▒ ▒▓▒ ▒ ░░░░ ▒░ ▒▒ ▒▒ ░ ░▓ ░   ██▒▒▒ ░▒▒ ▓░▒░▒", color.new(145, 197, 56), "Verkus.yaw", true)
client.log(" ░   ░ ░ ░   ▒▒ ░  ░      ░░ ░ ░  ░ ░▒  ░ ░░ ░ ░  ░ ░░   ░ ▒░░ ░▒  ░ ░░ ░ ░  ░  ░░   ░▒ ░ ▓██ ░▒░  ░▒ ▒ ░ ▒", color.new(145, 197, 56), "Verkus.yaw", true)
client.log(" ░   ░   ░   ▒  ░      ░       ░  ░  ░  ░      ░     ░   ░ ░ ░  ░  ░      ░  ░   ░    ░   ▒ ▒ ░░  ░ ░ ░ ░ ░", color.new(145, 197, 56), "Verkus.yaw", true)
client.log("     ░       ░         ░   ░   ░        ░  ░   ░           ░       ░  ░   ░   ░  ░    ░   ░ ░       ░ ░    ", color.new(145, 197, 56), "Verkus.yaw", true)
client.log("", color.new(145, 197, 56), "Verkus.yaw", true)
client.log("Welcome back, Verkus.yaw lua has been loaded.", color.new(145, 197, 56), "Verkus.Yaw", true)
client.log("Enjoy the Verkus.yaw experience.", color.new(145, 197, 56), "verkus.Yaw", true)
client.log("Last update: - Added     | User panel", color.new(145, 197, 56), "verkus.Yaw", true)
client.log("             - Added     | Watermark (by Verkus.yaw)", color.new(145, 197, 56), "verkus.Yaw", true)
client.log("             - Added     | Damage indicator", color.new(145, 197, 56), "verkus.Yaw", true)
client.log("             - Added     | Killsay", color.new(145, 197, 56), "Verkus.yaw", true)
client.log("", color.new(145, 197, 56), "Verkus.yaw", true)
client.log("Discord: https://discord.gg/w9Bc3RAzUS", color.new(145, 197, 56), "verkus.Yaw", true)

ui.add_label("| verkus.Yaw lua |")
ui.add_label("author: mayb.baby#8647")


render.fonts = {
    tahoma_13px = render.create_font("Tahoma", 13, 500, bit.bor(font_flags.dropshadow, font_flags.antialias));
}

render.screen = {
    w = 0,
    h = 0
}

render.center_screen = {
    w = 0,
    h = 0
}

render.update = function()
    local screen_size_x, screen_size_y = render.get_screen()

    render.screen.w = screen_size_x
    render.screen.h = screen_size_y

    render.center_screen.w = screen_size_x / 2
    render.center_screen.h = screen_size_y / 2
end
-- menu elements


local function round(num, numDecimalPlaces)
    local mult = 10^(numDecimalPlaces or 0)
    return math.floor(num * mult + 0.5) / mult
end
ui.add_label("")
ui.add_label("                 = anti-aim =                  ")


local enable_antiaim = ui.add_checkbox("Enable Verkus.yaw AA preset")
local roll_disable = ui.add_checkbox("SHIFT WALK  preset")

local cstrike = {
    cmd = nil,
    roll = 0
}

cstrike.update = function(pdr_cmd)
    cstrike.cmd = pdr_cmd
    cstrike.roll = pdr_cmd.viewangles.z
end

local globals = {
    local_player = nil,
    alive = nil,
    weapon = nil,
    weapon_type = nil,
    view_angles = nil,
    on_ground = nil
}

globals.update = function()
    globals.local_player = entity_list.get_client_entity(engine.get_local_player())
    globals.alive = client.is_alive()
    globals.weapon = entity_list.get_client_entity(globals.local_player:get_prop("DT_BaseCombatCharacter", "m_hActiveWeapon"))
    globals.weapon_type = globals.weapon:get_prop("DT_BaseAttributableItem", "m_iItemDefinitionIndex"):get_int()
    globals.view_angles = engine.get_view_angles()
end

cstrike.weapons = {
    deagle = 1,
    duals = 2,
    fiveseven = 3,
    glock = 4,
    awp = 9,
    g3sg1 = 11,
    tect9 = 30,
    p2000 = 32,
    p250 = 36,
    scar20 = 38,
    ssg08 = 40,
    revolver = 64,
    usp = 262205
}

cstrike.get_health = function(entity)
    if entity then
        local health = entity:get_prop("DT_BasePlayer", "m_iHealth"):get_int()
        return math.round(health)
    end

    return nil
end

cstrike.get_velocity = function(entity)
	if entity then
		local x = entity:get_prop("DT_BasePlayer", "m_vecVelocity[0]"):get_float()
		local y = entity:get_prop("DT_BasePlayer", "m_vecVelocity[1]"):get_float()

		return math.round(math.sqrt(x * x + y * y))
	end
end

cstrike.is_alive = function(entity)
    if entity then
        local health = cstrike.get_health(entity)
        if health > 0 then
            return true
        end
    end

    return false
end

cstrike.is_standing = function(entity)
	if entity then
		local is_moving = cstrike.is_moving(entity)
		if not is_moving then
			return true
		end
	end

	return false
end

cstrike.is_slowwalking = function(entity)
    if entity then
		if ui.get("Misc", "General", "Movement", "Slow motion key"):get_key() then
			return true
		end
    end

    return false
end


cstrike.is_crouching = function(entity)
    if entity then
        if cstrike.cmd:has_flag(4) then
            return true
        end
    end

    return false
end

cstrike.is_fake_ducking = function(entity)
    if entity then
        local duck_speed = entity:get_prop("DT_BasePlayer", "m_flDuckSpeed"):get_float()
        local duck_amount = entity:get_prop("DT_BasePlayer", "m_flDuckAmount"):get_float()

        if duck_speed == 8 and duck_amount > 0 and not cstrike.cmd:has_flag(1) then
            return true
        end
    end

    return false
end

cstrike.is_inair = function(entity)
	if entity then
        local local_player = entity_list.get_client_entity(engine.get_local_player())
		local ground_entity = local_player:get_prop("DT_BasePlayer", "m_hGroundEntity"):get_int()

		if ground_entity == -1 then
			return true
		end
	end

	return false
end

cstrike.is_moving = function(entity)
    local local_player = entity_list.get_client_entity(engine.get_local_player())
	if entity then
        local velocity = cstrike.get_velocity(entity)
		if velocity > 4 and not cstrike.is_inair(local_player)  then
			return true
		end
	end
    return false
end

cstrike.is_scoped = function(entity)
    if entity then
        local scoped = entity:get_prop("DT_CSPlayer", "m_bIsScoped"):get_int()
        if scoped == 1 then
            return true
        end
    end

    return false
end


math.radian_to_degree = function(radian)
    return radian * 180 / math.pi
end

math.degree_to_radian = function(degree)
    return degree * math.pi / 180
end

math.round = function(x)
    return x % 1 >= 0.5 and math.ceil(x) or math.floor(x)
end

math.normalize = function(angle)
    while angle < -180 do
        angle = angle + 360
    end

    while angle > 180 do
        angle = angle - 360
    end

    return angle
end

math.angle_to_vector = function(angle)
    local pitch = angle.x
    local yaw = angle.y

    return vector.new(math.cos(math.pi / 180 * pitch) * math.cos(math.pi / 180 * yaw), math.cos(math.pi / 180 * pitch) * math.sin(math.pi / 180 * yaw), -math.sin(math.pi / 180 * pitch))
end

math.calculate_angles = function(from, to)
	local sub = { 
		x = to.x - from.x, 
		y = to.y - from.y, 
		z = to.z - from.z 
	}

	local hyp = math.sqrt( sub.x * sub.x * 2 + sub.y * sub.y * 2 )

	local yaw = math.radian_to_degree( math.atan2( sub.y, sub.x ) );
	local pitch = math.radian_to_degree( -math.atan2( sub.z, hyp ) )

    return QAngle.new(pitch, yaw, 0)
end

math.calculate_fov = function(from, to, angles)
    local calculated = math.calculate_angles(from, to)

    local yaw_delta = angles.yaw - calculated.yaw;
    local pitch_delta = angles.pitch - calculated.pitch;

    if ( yaw_delta > 180 ) then
      yaw_delta = yaw_delta - 360
    end

    if ( yaw_delta < -180 ) then
      yaw_delta = yaw_delta + 360
    end

    return math.sqrt( yaw_delta * yaw_delta * 2 + pitch_delta * pitch_delta * 2 );
end
local utils = {}

utils.clamp = function(v, min, max)
    local num = v
    num = num < min and min or num
    num = num > max and max or num
    
    return num
end

utils.fluctuate = function(min, max)
    local used = false
    local ret = 0

    if used then
        ret = math.random(min, max)
        used = false
    else
        ret = math.random(min, max)
        used = true
    end

    return ret
end

utils.get_crosshair_target = function()
    if not globals.local_player then
        return
    end

    local data = {
        target = nil,
        fov = 180
    }

    local players = entity_list.get_all("CCSPlayer")
end
local antiaim = {}

antiaim.run = function()
    if not enable_antiaim:get() then
        return
    end

    local fake_yaw_type = ui.get("Rage", "Anti-aim", "General", "Fake yaw type")
    local body_yaw_limit = ui.get("Rage", "Anti-aim", "General", "Body yaw limit")
    local fake_yaw_limit = ui.get("Rage", "Anti-aim", "General", "Fake yaw limit")

    local yaw_jitter = ui.get("Rage", "Anti-aim", "General", "Yaw jitter")
    local yaw_jitter_conditions = ui.get("Rage", "Anti-aim", "General", "Yaw jitter conditions")
    local yaw_jitter_type = ui.get("Rage", "Anti-aim", "General", "Yaw jitter type")
    local yaw_jitter_range = ui.get("Rage", "Anti-aim", "General", "Yaw jitter range")

    local fake_yaw_direction = ui.get("Rage", "Anti-aim", "General", "Fake yaw direction")
    local yaw_additive = ui.get("Rage", "Anti-aim", "General", "Yaw additive")

    local body_roll = ui.get("Rage", "Anti-aim", "General", "Body roll")
    local body_roll_amount = ui.get("Rage", "Anti-aim", "General", "Body roll amount")
    local inverter_state = ui.get("Rage", "Anti-aim", "General", "Anti-aim invert")


    if cstrike.is_standing(globals.local_player) or cstrike.is_slowwalking(globals.local_player) then

        if roll_disable:get() then
            fake_yaw_direction:set(0)
            yaw_jitter:set(true)
            yaw_jitter_conditions:set("Standing", true)
            yaw_jitter_conditions:set("Walking", true)
            yaw_jitter_type:set(2)
            yaw_jitter_range:set(-38)
            body_yaw_limit:set(23)
            fake_yaw_limit:set(24)
            fake_yaw_type:set(1)
        else
            fake_yaw_direction:set(0)
            yaw_jitter:set(false)
            body_yaw_limit:set(60)
            fake_yaw_limit:set(60)
            fake_yaw_type:set(0)
            inverter_state:set_key(false)
        end

        if roll_disable:get() then
            body_roll:set(0)
        else
            body_roll:set(4)
        end
        if roll_disable:get() then
            yaw_additive:set(0)
        else
        if inverter_state:get_key( ) == false then
            body_roll_amount:set( -50 )
        else
            body_roll_amount:set( 50 )
        end
    end
    end

    if (cstrike.is_inair(globals.local_player) and not cstrike.is_moving(globals.local_player)) then 
        yaw_additive:set(0)
        yaw_jitter:set(true)
        yaw_jitter_conditions:set("In air", true)
        yaw_jitter_type:set(2)
        yaw_jitter_range:set(-34)
        fake_yaw_type:set(1)
        body_yaw_limit:set(42)
        fake_yaw_direction:set(0)
        body_roll:set(0)
    end

    if (not cstrike.is_slowwalking(globals.local_player) and cstrike.is_moving(globals.local_player)) then        
        yaw_additive:set(0)
        yaw_jitter:set(true)
        yaw_jitter_conditions:set("Moving", true)
        yaw_jitter_type:set(2)
        yaw_jitter_range:set(-42)
        fake_yaw_type:set(1)
        body_yaw_limit:set(60)
        fake_yaw_direction:set(0)
        body_roll:set(0)
    end

    if  (not cstrike.is_inair(globals.local_player) and cstrike.is_crouching(globals.local_player)) then
        yaw_additive:set(0)
        yaw_jitter:set(true)
        yaw_jitter_conditions:set("Moving", true)
        yaw_jitter_type:set(2)
        yaw_jitter_range:set(-44)
        fake_yaw_type:set(1)
        body_yaw_limit:set(46)
        fake_yaw_direction:set(0)
        body_roll:set(0)

        if roll_disable:get() then
            body_roll:set(0)
        else
            body_roll:set(4)
        end

        if inverter_state:get_key( ) == false then
            body_roll_amount:set( -50 )
        else
            body_roll_amount:set( 50 )
        end
    end
end

antiaim.handle_visibility = function()
    local state = enable_antiaim:get()
    local rol = roll_disable:get()

end
local on_post_move = function(cmd)
    globals.update()
    cstrike.update(cmd)

    antiaim.run()
end

callbacks.register("post_move", on_post_move)

ui.add_label("")
ui.add_label("                 = ragebot =                 ")
--UI--
local tickbase_boost = ui.add_checkbox("BOOST")
tickbase_boost:set(false)

--something--
local cmd_ticks = cvar.find_var("sv_maxusrcmdprocessticks")

--function--
function TickbaseBoost()
    if tickbase_boost:get() == true then
       cmd_ticks:set_value_int(19)          
    else
          cmd_ticks:set_value_int(16)  
    end    
end

--callbacks--
callbacks.register("post_move", TickbaseBoost)

-- menu elements.
local disable_lc_checkbox = ui.add_checkbox( "Enable anti-exploit" );

-- convars.
local cl_lagcompensation = cvar.find_var( "cl_lagcompensation" );

-- constants.
local TEAM_TERRORIST = 2;
local TEAM_CT = 3;

local function get_player_team( player )
    local m_iTeamNum = player:get_prop( "DT_BaseEntity", "m_iTeamNum" );

    return m_iTeamNum:get_int( );
end

-- https://github.com/perilouswithadollarsign/cstrike15_src/blob/f82112a2388b841d72cb62ca48ab1846dfcc11c8/game/shared/cstrike15/cs_gamerules.cpp#L15238
local function IsConnectedUserInfoChangeAllowed( player )
    local team_num = get_player_team( player );

    if team_num == TEAM_TERRORIST or team_num == TEAM_CT then
        return false;
    end

    return true;
end

-- cache.
local previous_dlc_state = disable_lc_checkbox:get( );

-- team swapping.
local changing_from_team = false;
local previous_team_num = -1;
local team_swap_time = -1;

local function on_paint( )
    -- get the local player's entity index.
    local local_player_idx = engine.get_local_player( );

    -- get the local player.
    local local_player = entity_list.get_client_entity( local_player_idx );

    -- will the server acknowledge our changes to cl_lagcompensation?
    if not engine.is_connected( ) or IsConnectedUserInfoChangeAllowed( local_player ) then
        -- update cl_lagcompensation accordingly.
        cl_lagcompensation:set_value_int( disable_lc_checkbox:get( ) and 0 or 1 );

        -- if we were on a team previously, we need to join that team again.
        if changing_from_team and global_vars.curtime > team_swap_time then
            -- join the team we were previously on.
            engine.execute_client_cmd( "jointeam " .. tostring( previous_team_num ) .. " 1" );

            -- we're no longer waiting to join our previous team.
            changing_from_team = false;
        end
    else
        -- have we clicked the checkbox while we were unable to change cl_lagcompensation?
        if disable_lc_checkbox:get( ) ~= previous_dlc_state then
            -- keep track of what team we're currently on.
            previous_team_num = get_player_team( local_player );

            -- join the spectator team.
            engine.execute_client_cmd( "spectate" );

            -- wait a bit before joining our team again so we don't get kicked for
            -- executing too many commands.
            changing_from_team = true;
            team_swap_time = global_vars.curtime + 1.5;

            -- cache the value of disable_lc_checkbox:get( ).
            previous_dlc_state = disable_lc_checkbox:get( );
        end
    end
end

-- init.
local function init( )
    callbacks.register( "paint", on_paint );
end
init( );



ui.add_label("")
ui.add_label("                  = visuals =                  ")


local indic_toggle = ui.add_checkbox("Enable indicators")
--local high_dpi_font = ui.add_checkbox("High DPI")

local indicators = {
    screen        = { render.get_screen() },
    screen_center = vector2d.new(0, 0),
    font_pixel    = render.create_font("Small Fonts", 8, 300, bit.bor(font_flags.outline)),
   -- high_dpi      = render.create_font("Verdana", 12, 100, bit.bor(font_flags.dropshadow, font_flags.antialias)),
    pulse_alpha   = 255,
    font_used     = font_pixel,
    refs = {
        baim = ui.get("Rage", "Aimbot", "Accuracy", "Force body-aim key"),
        fd = ui.get("Rage", "Anti-Aim", "Fake-lag", "Fake duck key"),
        dt = ui.get("Rage", "Exploits", "General", "Double tap key"),
        freestand = ui.get("Rage", "Anti-Aim", "General", "Freestanding key"),
        os = ui.get("Rage", "Exploits", "General", "Hide shots key"),
        dmg = ui.get("Rage", "Aimbot", "General", "Minimum damage override key")
    }
}

indicators.draw = function(table)
    for key, indicator in pairs(table) do
        key = key + 1

        local actual_index = key - 1 
        local font_size = { indicators.font_used:get_size(indicator.text) }

        indicators.font_used:text(
            render.center_screen.w + 6,
            render.center_screen.h + 6 + font_size[2] * actual_index,
            indicator.color,
            indicator.text
        )
    end
end


indicators.main = function()
    
    if not globals.local_player or not client.is_alive()  then
        return
    end

    if not indic_toggle:get() then
        return
    end
  --  indicators.font_used = indicators.high_dpi
  --  if not high_dpi_font:get() then
        indicators.font_used =  indicators.font_pixel
  --  end

    indicators.pulse_alpha = math.sin(math.abs((math.pi * -1) + (global_vars.curtime * 2.5) % (math.pi * 2))) * 255
    indicators.font_used:text( render.center_screen.w + 6, render.center_screen.h + 6, color.new(197, 204, 255, math.max(indicators.pulse_alpha, 25)), "Verkus.Yaw")


    indicators.indicators = {}


    
    if indicators.refs.dmg:get_key() then
        table.insert(
            indicators.indicators,
            {
                text = ("DMG"),
                color = color.new(197, 204, 255) 
            }
        )
    end

    if indicators.refs.freestand:get_key() then
        table.insert(
            indicators.indicators,
            {
                text = ("FREESTAND"),
                color = color.new(197, 204, 255)
            }
        )
    end

    if indicators.refs.os:get_key() then
        table.insert(
            indicators.indicators,
            {
                text = ("ONSHOT"),
                color = color.new(197, 204, 255)
            }
        )
    end


    if indicators.refs.fd:get_key() then
        table.insert(
            indicators.indicators,
            {
                text = ("DUCK"),
                color = color.new(197, 204, 255)
            }
        )
    end

    if indicators.refs.dt:get_key() then
        table.insert(
            indicators.indicators,
            {
                text = ("DT [" .. round(exploits.process_ticks() / exploits.max_process_ticks()*100, 0) .. "%]"),
                color = exploits.ready() and color.new(197, 204, 255) or color.new(255, 71, 71)
            }
        )
    end

    local body_roll_amount = ui.get("Rage", "Anti-aim", "General", "Body roll amount")

    if math.abs(cstrike.roll) > 0 then 
        table.insert(
            indicators.indicators,
            {
                text = ("ROLL"),
                color = color.new(255, 150, 255)
            }
        )
    end


    indicators.draw(indicators.indicators)
end


local elements = {
    [1] = "Static legs",
    [2] = "Pitch 0 on land",
    [3] = "Slide legs"
}

local cstrike = {}

cstrike.is_scoped = function(entity)
    if entity then
        local scoped = entity:get_prop("DT_CSPlayer", "m_bIsScoped"):get_int()
        if scoped == 1 then
            return true
        end
    end

    return false
end

local viewmodel_in_scope = ui.add_checkbox("Viewmodel in scope")


local on_paint = function()

    local fov_cs_debug = cvar.find_var("fov_cs_debug")

    if not viewmodel_in_scope:get() then
        fov_cs_debug:set_value_int(0)
        return
    end

    local local_player = entity_list.get_client_entity(engine.get_local_player())
    if not local_player then
        return
    end

    if cstrike.is_scoped(local_player) then
        fov_cs_debug:set_value_int(90)
    else
        fov_cs_debug:set_value_int(0)
    end
end

callbacks.register("paint", on_paint)

local displayMaxSpeed = ui.add_dropdown("Slowed down indicator (sigma style)", {"Disabled", "Enabled"})
local interval = 0

local function rgb_health_based(percentage)
    local r = 124*2 - 124 * percentage
    local g = 195 * percentage
    local b = 13
    return r, g, b
end

local function remap(val, newmin, newmax, min, max, clamp)
    min = min or 0
    max = max or 1

    local pct = (val-min)/(max-min)

    if clamp ~= false then
        pct = math.min(1, math.max(0, pct))
    end

    return newmin+(newmax-newmin)*pct
end

local function rectangle_outline(x, y, w, h, r, g, b, a, s)
    s = s or 1
    render.rectangle(x, y, w, s, color.new(r, g, b, a)) -- top
    render.rectangle(x, y+h-s, w, s, color.new(r, g, b, a)) -- bottom
    render.rectangle(x, y+s, s, h-s*2, color.new(r, g, b, a)) -- left
    render.rectangle(x+w-s, y+s, s, h-s*2, color.new(r, g, b, a)) -- right
end

local function drawBar(modifier, r, g, b, a, text)
    local text_width = 95
    local sw, sh = render.get_screen()
    local x, y = sw/2-text_width, sh*0.35

    if a > 0.7 then
        render.rectangle(x+13, y+11, 8, 20, color.new(16, 16, 16, 255*a))
    end

    render.text(x+8, y+3, string.format("%s %.f", text, modifier * 100.0), color.new(255, 255, 255, 255*a))

    local rx, ry, rw, rh = x+8, y+3+17, text_width, 12
    rectangle_outline(rx, ry, rw, rh, 0, 0, 0, 255*a, 1)
    render.rectangle_filled(rx+1, ry+1, rw-2, rh-2, color.new(16, 16, 16, 180*a))
    render.rectangle_filled(rx+1, ry+1, math.floor((rw-2)*modifier), rh-2, color.new(r, g, b, 180*a))
end

callbacks.register("paint", function()
    local lp = entity_list.get_client_entity(engine.get_local_player())
    if not client.is_alive() then return end

    local modifier = lp:get_prop("DT_CSPlayer", "m_flVelocityModifier"):get_float()
    if modifier == 1 then return end

    local r, g, b = rgb_health_based(modifier)
    local a = remap(modifier, 1, 0, 0.85, 1)

    if displayMaxSpeed:get() == 1 then
        drawBar(modifier, r, g, b, a, "Slowed down")
    end
end)


local font = render.create_font("Verdana", 12, 400, bit.bor(font_flags.outline))
--Menu
local indicator_checkbox = ui.add_checkbox("Enable user panel")

-- Var
local g_col_disabled = color.new(153,124,122);
local g_col_enabled  = color.new(153,124,122);
local lag_history = {0, 0, 0, 0, 0, 0}
-- UI GET
local jitter = ui.get("Rage","Anti-Aim","General","Yaw jitter")
local exploit = ui.get("Rage", "Exploits", "General", "Enabled")
local dt = ui.get("Rage", "Exploits", "General", "Double tap key")
local dmg = ui.get_rage("General", "Minimum damage override key")
local fs = ui.get("Rage", "Anti-aim", "General", "Freestanding key")
local fd = ui.get("Rage", "Anti-aim", "Fake-lag", "Fake duck key")
local sw = ui.get("Misc", "General", "Movement", "Slow motion key")


local function drawBase()
if indicator_checkbox:get() == true then
    font:text(30, 450, color.new(153,120,92),"Verkus.Yaw lua - version 1.0.0")
    font:text(30, 465, color.new(132,113,145),"> anti-aim info :")
    font:text(30, 480, color.new(153,124,122),"> rage-bot info :")
    font:text(30, 495, color.new(154,156,134),"> player info : state - ")
    end 
end
local function drawFl()
        if client.choked_commands() < lag_history[6] then
            lag_history[1] = lag_history[2]
             lag_history[2] = lag_history[3]
             lag_history[3] = lag_history[4]
             lag_history[4] = lag_history[5]
             lag_history[5] = lag_history[6]
        end
        font:text(153,465, color.new(115,109,153), string.format("fl(%i-%i-%i)",lag_history[5],lag_history[4],lag_history[3],lag_history[2],lag_history[1]  ))
        lag_history[6] = client.choked_commands()
end
local function drawSide()
    if anti_aim.inverted() then
        font:text(223, 465, color.new(115,109,153), "side : > ")     
    else
        font:text(223, 465, color.new(115,109,153), "side : < ")
    end
end
local function drawAA()
    if not fs:get_key() then
        font:text(125, 465, color.new(118,109,153),"jitter")
        return
    elseif jitter:get() == true then
        font:text(125, 465, color.new(118,109,153),"freestanding")
    else
        font:text(125, 465, color.new(118,109,153),"static")
    end
end

local function getMinimumDamage( var )
    local minimum_damage = var:get();
    if minimum_damage == 0 then
        return "auto";
    elseif minimum_damage > 100 then
        return string.format("hp+%d", minimum_damage - 100);
    else
        return tostring(minimum_damage);
    end
end
local function drawDmg()
    local is_overriding = dmg:get_key();
    local dmg1 = ui.get_rage("General", "Minimum damage")
    local dmg2 = ui.get_rage("General", "Minimum damage override")
    local v = getMinimumDamage(is_overriding and dmg2 or dmg1);
    font:text(123, 480, is_overriding and g_col_enabled or g_col_disabled, string.format("dmg: %s", v));
   
end
local function drawDt()
    if not exploit:get() then
        return
    end
    if not dt:get_key() then
        font:text(175, 480, color.new(153,124,122),"dt")
        return
    end
    local doubletap_value = exploits.process_ticks() / 14;
    font:text( 175, 480, color.new(153,124,122), string.format("dt (%d%s)", math.floor(doubletap_value * 100), "%"));
end 
local function drawPlayer()
   if sw:get_key() then
    font:text(150, 495, color.new(154,156,134),"slow walk")
   end
   if fd:get_key() then
    font:text(150, 495, color.new(154,156,134),"fake duck")
   end
   if not sw:get_key() and not fd:get_key() then
    font:text(150, 495, color.new(154,156,134),"native")
   end  
end
-- end indicator 

local function onPaint()
if indicator_checkbox:get() == true then
    if not client.is_alive() then
        return
    end
   drawBase();
   drawFl();
   drawSide();
   drawAA();
   drawDmg();
   drawDt();
   drawPlayer();
end
end
callbacks.register("paint", onPaint);

local indicator_checkbox = ui.add_checkbox("Damage indicator")

-- Var
local g_col_disabled = color.new(255,255,255);
local g_col_enabled  = color.new(255,255,255);

-- Screensize
local screen_width, screen_height = render.get_screen( );
local center_x = ( screen_width / 2 );
local center_y = ( screen_height / 2);

local dmg = ui.get_rage("General", "Minimum damage override key")

local function getMinimumDamage( var )
    local minimum_damage = var:get();
    if minimum_damage == 0 then
        return "auto";
    elseif minimum_damage > 100 then
        return string.format("10%d", minimum_damage - 100);
    else
        return tostring(minimum_damage);
    end
end
local function drawDmg()
    local is_overriding = dmg:get_key();
    local dmg1 = ui.get_rage("General", "Minimum damage")
    local dmg2 = ui.get_rage("General", "Minimum damage override")
    local v = getMinimumDamage(is_overriding and dmg2 or dmg1);
    font:text(center_x - 15, center_y - 20, is_overriding and g_col_enabled or g_col_disabled, string.format("%s", v));
   
end


local function onPaint()
if indicator_checkbox:get() == true then
    if not client.is_alive() then
        return
    end
   drawDmg();
end
end
callbacks.register("paint", onPaint);



local small_fonts = render.create_font( "Small Fonts", 9, 400, font_flags.dropshadow );
local world_hitmarker_dmg = ui.add_checkbox( "Hitmarker" );

local markers = { }

function on_paint( )
    if not world_hitmarker_dmg:get( ) then
        return
    end

    local step = 255.0 / 1.0 * global_vars.frametime;
    local step_move = 30.0 / 1.5 * global_vars.frametime;
    local multiplicator = 0.3;

    for idx = 1, #markers do
        local marker = markers[ idx ];

        if marker == nil then
            return
        end

        marker.moved = marker.moved - step_move;

        if marker.create_time + 0.5 <= global_vars.curtime then
            marker.alpha = marker.alpha - step;
        end

        if marker.alpha > 0 then
            local screen_position = vector2d.new( 0, 0 );

            if render.world_to_screen( marker.world_position, screen_position ) then
                small_fonts:text( screen_position.x + 8, screen_position.y - 12 + marker.moved, color.new( 163, 146, 255, marker.alpha ), "-" .. marker.dmg );
            end
        else
            table.remove( markers, idx );
        end
    end
end

function on_hitmarker( damage, position )
    table.insert( markers, {
        dmg = damage,
        world_position = vector.new( position.x, position.y, position.z ),
        create_time = global_vars.curtime,
        moved = 0.0,
        alpha = 255.0
    } );
end

callbacks.register( "on_hitmarker", on_hitmarker );
callbacks.register( "paint", on_paint );

local dist_ref = ui.add_slider("Thirdperson distance", 0, 200)
local get_cam_idealdist = cvar.find_var("cam_idealdist")

callbacks.register("paint", function()
   get_cam_idealdist:set_value_int(dist_ref:get())
end)




ui.add_label("")
ui.add_label("                    = misc =                    ")



local animations = {
    on_land = false,
    static_legs_on = false,
    pitch_land_on = false,
    sliding_legs_on = false,
    options =  ui.add_multi_dropdown("Custom animations", { elements[1], elements[2], elements[3] })
}

animations.main = function(ent)

    if ent:index() ~= engine.get_local_player() or not globals.local_player or not client.is_alive()  then
        return
    end

    animations.static_legs_on = animations.options:get(elements[1])
    animations.pitch_land_on = animations.options:get(elements[2])
    animations.sliding_legs_on = animations.options:get(elements[3])


    animations.sliding_legs(ent)
    animations.static_legs(ent)
    animations.pitch_land(ent)
end


animations.sliding_legs = function(ent)

    if not animations.sliding_legs_on then
        return
    end

    local m_flPoseParameter = ent:get_prop("DT_BaseAnimating", "m_flPoseParameter")
    m_flPoseParameter:set_float_index(0, 1)
end

animations.static_legs = function(ent)

    if not animations.static_legs_on then
        return
    end

    local m_flPoseParameter = ent:get_prop("DT_BaseAnimating", "m_flPoseParameter")
    m_flPoseParameter:set_float_index(6, 1)
end

animations.pitch_land = function(ent)

    if not animations.pitch_land_on then
        return
    end

    if not animations.on_land then
        return
    end
    
    local m_flPoseParameter = ent:get_prop("DT_BaseAnimating", "m_flPoseParameter")
    m_flPoseParameter:set_float_index(12, 0.45)
end

local ground_ticks = 0
local end_time = 0

animations.update_land = function()

    if not globals.local_player or not client.is_alive() then
        return
    end

    local on_ground = bit.band(globals.local_player:get_prop("DT_BasePlayer", "m_fFlags"):get_int(), 1)

    if on_ground == 1 then
        ground_ticks = ground_ticks + 1
    else
        ground_ticks = 0
        end_time = global_vars.curtime + 1
    end 

    animations.on_land = false

    if ground_ticks > 2 and end_time > global_vars.curtime then
        animations.on_land = true
    end

end

local x, y=render.get_screen()

local lua={

    menu={
        watermark=ui.add_checkbox("Enable watermark"),
        color=ui.add_cog("Watermark", true, false),
    },

    get_tickrate=function()
        if not engine.is_connected() then return 0 end
        return math.floor(1.0/global_vars.interval_per_tick)
    end,

    watermark_rect=function(x, y, w, h, color)
        render.rectangle_filled(x, y, w, 2, color)
        render.rectangle_filled(x, y, w, h-2, color.new(0, 0, 0, 120))
    end,

    font={
        segoe_ui=render.create_font("SegoUI", 13, 700, bit.bor(font_flags.dropshadow, font_flags.antialias)),
    },
    
}

function watermark()
    if not lua.menu.watermark:get() then return end
    local text=string.format("verkus.Yaw | %s | rate: %s | ms: %s | %s", client.get_username, tostring(lua.get_tickrate()), tostring(client.latency()+0), client.local_time("%H:%M:%S"))
    local text_size={lua.font.segoe_ui:get_size(text)}
    lua.watermark_rect(x-text_size[1]-15, 8, text_size[1]+10, text_size[2]+5, lua.menu.color:get_color())
    lua.font.segoe_ui:text(x-text_size[1]-10, 10, color.new(255, 255, 255, 255),text)
end

function on_paint()
    watermark()
end

callbacks.register("paint", on_paint)


local font = render.create_font("Verdana", 12, 250, bit.bor(font_flags.outline))

local best_killsay = ui.add_checkbox("Enable killsay")

function on_player_death(event)
    if not best_killsay:get() then
        return
    end

    local phrases = {
        "1 by the best lua",
        "verkus.Yaw lua on top",
        "1 HUISOS BY verkus.Yaw",
        "too easy for verkus.Yaw lua",
        "bad?"
    }
    

    local userid = event:get_int("userid")
    local attacker = event:get_int("attacker")
    local local_player = engine.get_local_player()
    local attacker_entindex = engine.get_player_for_user_id(attacker)
    local victim_entindex = engine.get_player_for_user_id(userid)

    if attacker_entindex ~= local_player or victim_entindex == local_player then
        return
    end

    engine.execute_client_cmd("say " .. phrases[math.random(1,5, #phrases)])
end

callbacks.register("player_death", on_player_death)


local on_paint = function()
    render.update()
    indicators.main()
    antiaim.handle_visibility()
    animations.update_land()
end

callbacks.register("paint", on_paint)


callbacks.register("post_anim_update", animations.main)

-- menu elements.
local party_mode_checkbox = ui.add_checkbox( "Party zeus" );

-- cvars.
local sv_party_mode = cvar.find_var( "sv_party_mode" );

-- callbacks.
local function on_paint( )
    sv_party_mode:set_value_int( ( party_mode_checkbox:get() and 1 or 0 ) );
end

-- init.
local function init( )
    callbacks.register( "paint", on_paint );
end
init( );