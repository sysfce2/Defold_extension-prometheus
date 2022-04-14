# extension-prometheus
Lua obfuscation using [Prometheus](https://github.com/levno-710/Prometheus). This extension hooks into the Lua builder plugin system in bob.


## Prometheus config
The extension is running Prometheus with the following configuration:

```bash
lua cli.lua --preset Weak --out out.lua in.lua 
```

```lua
local test = require("main.test")

function init(self)
 print("hello")
 test.greet("Bob")
end
```

```lua
local q={"Bob","main.test","greet","hello"}do local h,Q=1,4 while h<Q do q[h],q[Q]=q[Q],q[h]h,Q=h+1,Q-1 end h,Q=1,2 while h<Q do q[h],q[Q]=q[Q],q[h]h,Q=h+1,Q-1 end h,Q=3,4 while h<Q do q[h],q[Q]=q[Q],q[h]h,Q=h+1,Q-1 end end local function Q(h)return q[h+2201]end local h=require(Q(-2197))function init(q)print(Q(-2199))h[Q(-2200)](Q(-2198))end
```


## Prometheus source code
Prometheus source code is packaged into `pluginPrometheusSource.jar` and unpacked using `getResourceAsStream()` to a temporary folder while bob is running.

