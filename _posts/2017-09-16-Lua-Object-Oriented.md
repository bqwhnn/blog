---
layout: post
title: "Lua 面向对象"
description:
categories: [tutorials]
tags: [lua]
redirect_from:
  - /2017/09/16
---

* Kramdown table of contents
{:toc .toc}

# 简单的实例

~~~ lua
function class(classname, super)
	local superType = type(super)
	local cls
	
	if superType ~= "function" and superType ~= "table" then
		superType = nil
		super = nil
	end
	
	-- inherited from Lua Object
	if super then
		cls = {}
		setmetatable(cls, {__index = super})
		cls.super = super
	else
		cls = {ctor = function() end}
	end
	
	cls.__cname = classname
	cls.__index = cls
	
	function cls.new(...)
		local obj_data = {}
		local cls_name = cls.__cname
		
		local instance = setmetatable(obj_data, cls)
		instance.class = cls
		instance:ctor(...)
		return instance
	end
	return cls
end
~~~