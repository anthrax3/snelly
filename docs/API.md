
## Classes

<dl>
<dt><a href="#Snelly">Snelly</a></dt>
<dd></dd>
<dt><a href="#Scene">Scene</a></dt>
<dd></dd>
<dt><a href="#Renderer">Renderer</a></dt>
<dd></dd>
<dt><a href="#Material">Material</a></dt>
<dd></dd>
<dt><a href="#Surface">Surface</a> ⇐ <code><a href="#Material">Material</a></code></dt>
<dd></dd>
<dt><a href="#Metal">Metal</a> ⇐ <code><a href="#Material">Material</a></code></dt>
<dd></dd>
<dt><a href="#Dielectric">Dielectric</a> ⇐ <code><a href="#Material">Material</a></code></dt>
<dd></dd>
<dt><a href="#Materials">Materials</a></dt>
<dd></dd>
</dl>

## Objects

<dl>
<dt><a href="#GLU">GLU</a> : <code>object</code></dt>
<dd><p>Namespace for webGL utility wrappers.
Functions for loading shader uniform variables are exposed to the user
for convenience.</p>
</dd>
</dl>

<a name="Snelly"></a>

## Snelly
**Kind**: global class  

* [Snelly](#Snelly)
    * [new Snelly(sceneObj)](#new_Snelly_new)
    * [.getVersion()](#Snelly+getVersion) ⇒ <code>Array</code>
    * [.getRenderer()](#Snelly+getRenderer) ⇒ [<code>Renderer</code>](#Renderer)
    * [.getGUI()](#Snelly+getGUI) ⇒ <code>GUI</code>
    * [.getCamera()](#Snelly+getCamera) ⇒ <code>THREE.PerspectiveCamera</code>
    * [.getControls()](#Snelly+getControls) ⇒ <code>THREE.OrbitControls</code>
    * [.showGUI(show)](#Snelly+showGUI)
    * [.getMaterials()](#Snelly+getMaterials) ⇒ [<code>Materials</code>](#Materials)
    * [.getSurface()](#Snelly+getSurface) ⇒ [<code>Surface</code>](#Surface)

<a name="new_Snelly_new"></a>

### new Snelly(sceneObj)
Snelly is the global object providing access to all functionality in the system.


| Param | Type | Description |
| --- | --- | --- |
| sceneObj | [<code>Scene</code>](#Scene) | The user-defined scene |

<a name="Snelly+getVersion"></a>

### snelly.getVersion() ⇒ <code>Array</code>
Returns the current version number of the snelly system, in the format [1, 2, 3]

**Kind**: instance method of [<code>Snelly</code>](#Snelly)  
<a name="Snelly+getRenderer"></a>

### snelly.getRenderer() ⇒ [<code>Renderer</code>](#Renderer)
Access to the Renderer object

**Kind**: instance method of [<code>Snelly</code>](#Snelly)  
<a name="Snelly+getGUI"></a>

### snelly.getGUI() ⇒ <code>GUI</code>
Access to the GUI object

**Kind**: instance method of [<code>Snelly</code>](#Snelly)  
<a name="Snelly+getCamera"></a>

### snelly.getCamera() ⇒ <code>THREE.PerspectiveCamera</code>
Access to the camera object

**Kind**: instance method of [<code>Snelly</code>](#Snelly)  
**Returns**: <code>THREE.PerspectiveCamera</code> - .  
<a name="Snelly+getControls"></a>

### snelly.getControls() ⇒ <code>THREE.OrbitControls</code>
Access to the camera controller object

**Kind**: instance method of [<code>Snelly</code>](#Snelly)  
**Returns**: <code>THREE.OrbitControls</code> - .  
<a name="Snelly+showGUI"></a>

### snelly.showGUI(show)
Programmatically show or hide the dat.GUI UI

**Kind**: instance method of [<code>Snelly</code>](#Snelly)  

| Param | Type | Description |
| --- | --- | --- |
| show | <code>Boolean</code> | toggle |

<a name="Snelly+getMaterials"></a>

### snelly.getMaterials() ⇒ [<code>Materials</code>](#Materials)
Get materials object

**Kind**: instance method of [<code>Snelly</code>](#Snelly)  
<a name="Snelly+getSurface"></a>

### snelly.getSurface() ⇒ [<code>Surface</code>](#Surface)
Get Surface object

**Kind**: instance method of [<code>Snelly</code>](#Snelly)  
<a name="Scene"></a>

## Scene
**Kind**: global class  

* [Scene](#Scene)
    * [.init(snelly)](#Scene+init)
    * [.initGenerator()](#Scene+initGenerator)
    * [.envMap()](#Scene+envMap) ⇒ <code>String</code>
    * [.getName()](#Scene+getName) ⇒ <code>String</code>
    * [.getURL()](#Scene+getURL) ⇒ <code>String</code>
    * [.shader()](#Scene+shader) ⇒ <code>String</code>
    * [.initGui(gui)](#Scene+initGui)
    * [.syncShader(shader)](#Scene+syncShader)
    * [.getMinScale()](#Scene+getMinScale) ⇒ <code>number</code>
    * [.getMaxScale()](#Scene+getMaxScale) ⇒ <code>number</code>
    * [.preframeCallback(snelly, gl)](#Scene+preframeCallback)
    * [.postframeCallback(snelly, gl)](#Scene+postframeCallback)

<a name="Scene+init"></a>

### scene.init(snelly)
Optionally (but usually), provide this function to set scene and renderer initial state.

**Kind**: instance method of [<code>Scene</code>](#Scene)  

| Param | Type | Description |
| --- | --- | --- |
| snelly | [<code>Snelly</code>](#Snelly) | The snelly object |

<a name="Scene+initGenerator"></a>

### scene.initGenerator()
Optionally, provide this function which generates the init code to re-generate 

**Kind**: instance method of [<code>Scene</code>](#Scene)  
<a name="Scene+envMap"></a>

### scene.envMap() ⇒ <code>String</code>
Optionally, supply an env-map texture URL (must be a lat-long format image).

**Kind**: instance method of [<code>Scene</code>](#Scene)  
<a name="Scene+getName"></a>

### scene.getName() ⇒ <code>String</code>
Optional name (displayed in UI)

**Kind**: instance method of [<code>Scene</code>](#Scene)  
<a name="Scene+getURL"></a>

### scene.getURL() ⇒ <code>String</code>
Optional clickable URL (displayed in UI)

**Kind**: instance method of [<code>Scene</code>](#Scene)  
<a name="Scene+shader"></a>

### scene.shader() ⇒ <code>String</code>
Returns a chunk of GLSL code defining the SDFs which determine the geometry of uber-surface, metal and dielectric materials in the scene.
		// return surface diffuse reflectance (defaults to just return the input UI constant C)
		vec3 SURFACE_DIFFUSE_REFLECTANCE(in vec3 C, in vec3 X, in vec3 N, in vec3 V);

		// return surface specular reflectance (defaults to just return the input UI constant C)
		vec3 SURFACE_SPECULAR_REFLECTANCE(in vec3 C, in vec3 X, in vec3 N, in vec3 V);

		// return surface roughness in [0,1] (defaults to just return the input roughness)
		float SURFACE_ROUGHNESS(in float roughness, in vec3 X, in vec3 N);

		// return metal roughness in [0,1] (defaults to just return the input UI constant roughness)
		float METAL_ROUGHNESS(in float roughness, in vec3 X, in vec3 N);

		// return metal specular reflectance (defaults to just return the input C)
		vec3 METAL_SPECULAR_REFLECTANCE(in vec3 C, in vec3 X, in vec3 N, in vec3 V);

		// return dielectric roughness in [0,1] (defaults to just return the input UI constant roughness)
		float DIELECTRIC_ROUGHNESS(in float roughness, in vec3 X, in vec3 N);

		// return dielectric specular reflectance (defaults to just return the input UI constant C)
		vec3 DIELECTRIC_SPECULAR_REFLECTANCE(in vec3 C, in vec3 X, in vec3 N, in vec3 V);

Optionally, an init function can be provided, which will be called first by each primary ray. 
This is occasionally useful to prepare global variables for use during the succeeding computation for this pixel.
	void INIT();

**Kind**: instance method of [<code>Scene</code>](#Scene)  
<a name="Scene+initGui"></a>

### scene.initGui(gui)
Optional. Set up gui and callbacks for this scene

**Kind**: instance method of [<code>Scene</code>](#Scene)  

| Param | Type | Description |
| --- | --- | --- |
| gui | <code>GUI</code> | wrapper for dat.GUI object |

<a name="Scene+syncShader"></a>

### scene.syncShader(shader)
Optional. Called whenever the UI is changed,
/* and must sync the params of the shader with the current UI settings

**Kind**: instance method of [<code>Scene</code>](#Scene)  

| Param | Type | Description |
| --- | --- | --- |
| shader | <code>Shader</code> | wrapper of webGL fragment shader |

<a name="Scene+getMinScale"></a>

### scene.getMinScale() ⇒ <code>number</code>
Optional. Gives the raytracer some indication of the (rough) minimum length scale, 

**Kind**: instance method of [<code>Scene</code>](#Scene)  
<a name="Scene+getMaxScale"></a>

### scene.getMaxScale() ⇒ <code>number</code>
Optional. Gives the raytracer some indication of the (rough) maximum length scale, 

**Kind**: instance method of [<code>Scene</code>](#Scene)  
<a name="Scene+preframeCallback"></a>

### scene.preframeCallback(snelly, gl)
Optional callback before every frame.

**Kind**: instance method of [<code>Scene</code>](#Scene)  

| Param | Type | Description |
| --- | --- | --- |
| snelly | [<code>Snelly</code>](#Snelly) | The Snelly object |
| gl | <code>WebGLRenderingContext</code> | The webGL context |

<a name="Scene+postframeCallback"></a>

### scene.postframeCallback(snelly, gl)
Optional callback after every frame.

**Kind**: instance method of [<code>Scene</code>](#Scene)  

| Param | Type | Description |
| --- | --- | --- |
| snelly | [<code>Snelly</code>](#Snelly) | The Snelly object |
| gl | <code>WebGLRenderingContext</code> | The webGL context |

<a name="Renderer"></a>

## Renderer
**Kind**: global class  
**Properties**

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| width | <code>number</code> |  | (if not specified, fits to window) |
| height | <code>number</code> |  | (if not specified, fits to window) |
| renderMode | <code>String</code> | <code>&#x27;pt&#x27;</code> | rendering mode (either 'pt', 'ao', 'normals', 'diffuse') |
| maxMarchSteps | <code>number</code> | <code>256</code> | maximum number of raymarching steps per path segment |
| radianceClamp | <code>number</code> | <code>3.0</code> | clamp radiance to (10^) this max value, for firefly reduction |
| skyPower | <code>number</code> | <code>4.0</code> | sky power (arbitrary units) |
| skyTemperature | <code>number</code> | <code>6000</code> | sky temperature (in Kelvin) |
| exposure | <code>number</code> | <code>4.5</code> | exposure, on a log scale |
| gamma | <code>number</code> | <code>2.2</code> | display gamma correction |
| whitepoint | <code>number</code> | <code>2.0</code> | tonemapping whitepoint |
| goalFPS | <code>number</code> | <code>10.0</code> | sampling will adjust to try to match goal FPS |
| minsSPPToRedraw | <code>number</code> | <code>0.0</code> | if >0.0, renderer will not redraw until the specified SPP have been accumulated |
| envMapVisible | <code>number</code> | <code>true</code> | whether env map is visible to primary rays (otherwise black) |
| envMapRotation | <code>number</code> | <code>0.0</code> | env map rotation about pole in degrees (0 to 360) |
| shadowStrength | <code>number</code> | <code>1.0</code> | if <1.0, areas in shadow are not completely dark (provided mostly to allow rendering of occluded areas, e.g. fractals) |
| maxStepsIsMiss | <code>number</code> | <code>true</code> | whether rays which exceed max step count are considered hits or misses |
| AA | <code>number</code> | <code>true</code> | whether to jitter primary ray within pixel for AA |


* [Renderer](#Renderer)
    * [new Renderer()](#new_Renderer_new)
    * [.reset([no_recompile])](#Renderer+reset)
    * [.getSPP()](#Renderer+getSPP) ⇒ <code>number</code>

<a name="new_Renderer_new"></a>

### new Renderer()
Interface to the renderer. The rendering modes available are:

<a name="Renderer+reset"></a>

### renderer.reset([no_recompile])
Restart accumulating samples.

**Kind**: instance method of [<code>Renderer</code>](#Renderer)  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| [no_recompile] | <code>Boolean</code> | <code>false</code> | set to true if shaders need recompilation too |

<a name="Renderer+getSPP"></a>

### renderer.getSPP() ⇒ <code>number</code>
Read access to the current per-pixel sample count average.

**Kind**: instance method of [<code>Renderer</code>](#Renderer)  
**Returns**: <code>number</code> - - the current sample count average  
<a name="Material"></a>

## Material
**Kind**: global class  
<a name="new_Material_new"></a>

### new Material()
Generic material.

<a name="Surface"></a>

## Surface ⇐ [<code>Material</code>](#Material)
**Kind**: global class  
**Extends**: [<code>Material</code>](#Material)  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| roughness | <code>number</code> | The surface roughness |
| ior | <code>number</code> | The surface coating ior |
| diffuseAlbedo | <code>Array</code> | The surface diffuse (RGB) color |
| specAlbedo | <code>Array</code> | The surface spec (RGB) color |

<a name="new_Surface_new"></a>

### new Surface()
Generic uber-surface material. Control via properties:

**Example**  
```js
surface.roughness = 0.05;
```
<a name="Metal"></a>

## Metal ⇐ [<code>Material</code>](#Material)
**Kind**: global class  
**Extends**: [<code>Material</code>](#Material)  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| roughness | <code>number</code> | The metal surface roughness |

<a name="new_Metal_new"></a>

### new Metal()
Generic metal material. Supported physical metals are:

**Example**  
```js
let metal = materials.loadMetal('Gold');
```
<a name="Dielectric"></a>

## Dielectric ⇐ [<code>Material</code>](#Material)
**Kind**: global class  
**Extends**: [<code>Material</code>](#Material)  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| roughness | <code>number</code> | The dielectric surface roughness |
| absorptionColor | <code>array</code> | The dielectric surface absorption color |
| absorptionScale | <code>number</code> | The dielectric surface absorption scale (m.f.p in multiples of scene max scale) |

<a name="new_Dielectric_new"></a>

### new Dielectric()
Generic dielectric material. Supported physical dielectrics are:

**Example**  
```js
let dielectric = materials.loadDielectric('Diamond');
```
<a name="Materials"></a>

## Materials
**Kind**: global class  

* [Materials](#Materials)
    * [new Materials()](#new_Materials_new)
    * [.loadDielectric(dielectricName)](#Materials+loadDielectric) ⇒ [<code>Dielectric</code>](#Dielectric)
    * [.loadMetal(metalName)](#Materials+loadMetal) ⇒ [<code>Metal</code>](#Metal)
    * [.getDielectric()](#Materials+getDielectric) ⇒ [<code>Dielectric</code>](#Dielectric)
    * [.getMetal()](#Materials+getMetal) ⇒ [<code>Metal</code>](#Metal)
    * [.getSurface()](#Materials+getSurface) ⇒ [<code>Surface</code>](#Surface)

<a name="new_Materials_new"></a>

### new Materials()
This object controls the properties of the three basic material types:

<a name="Materials+loadDielectric"></a>

### materials.loadDielectric(dielectricName) ⇒ [<code>Dielectric</code>](#Dielectric)
Load the desired Dielectric object by name. Supported dielectrics are:

**Kind**: instance method of [<code>Materials</code>](#Materials)  
**Returns**: [<code>Dielectric</code>](#Dielectric) - - the loaded dielectric  

| Param | Type | Description |
| --- | --- | --- |
| dielectricName | <code>String</code> | one of the names listed above |

<a name="Materials+loadMetal"></a>

### materials.loadMetal(metalName) ⇒ [<code>Metal</code>](#Metal)
Load the desired Metal object by name. Supported metals are:

**Kind**: instance method of [<code>Materials</code>](#Materials)  
**Returns**: [<code>Metal</code>](#Metal) - - the loaded metal  

| Param | Type | Description |
| --- | --- | --- |
| metalName | <code>String</code> | one of the names listed above |

<a name="Materials+getDielectric"></a>

### materials.getDielectric() ⇒ [<code>Dielectric</code>](#Dielectric)
Get the currently loaded Dielectric object.

**Kind**: instance method of [<code>Materials</code>](#Materials)  
<a name="Materials+getMetal"></a>

### materials.getMetal() ⇒ [<code>Metal</code>](#Metal)
Get the currently loaded Metal object.

**Kind**: instance method of [<code>Materials</code>](#Materials)  
<a name="Materials+getSurface"></a>

### materials.getSurface() ⇒ [<code>Surface</code>](#Surface)
Get the Surface object.

**Kind**: instance method of [<code>Materials</code>](#Materials)  
<a name="GLU"></a>

## GLU : <code>object</code>
Namespace for webGL utility wrappers.

**Kind**: global namespace  

* [GLU](#GLU) : <code>object</code>
    * [.this.Shader](#GLU.this.Shader)
        * [new this.Shader()](#new_GLU.this.Shader_new)
        * [.uniformI(name, i)](#GLU.this.Shader.uniformI)
        * [.uniformF(name, f)](#GLU.this.Shader.uniformF)
        * [.uniform2F(name, f1, f2)](#GLU.this.Shader.uniform2F)
        * [.uniform1Fv(name, fvec)](#GLU.this.Shader.uniform1Fv)
        * [.uniform2Fv(name, fvec2)](#GLU.this.Shader.uniform2Fv)
        * [.uniform3F(name, f1, f2, f3)](#GLU.this.Shader.uniform3F)
        * [.uniform3Fv(name, fvec3)](#GLU.this.Shader.uniform3Fv)
        * [.uniform4F(name, f1, f2, f3, f4)](#GLU.this.Shader.uniform4F)
        * [.uniform4Fv(name, fvec4)](#GLU.this.Shader.uniform4Fv)
        * [.uniformMatrix4fv(name, matrixArray16)](#GLU.this.Shader.uniformMatrix4fv)

<a name="GLU.this.Shader"></a>

### GLU.this.Shader
**Kind**: static class of [<code>GLU</code>](#GLU)  

* [.this.Shader](#GLU.this.Shader)
    * [new this.Shader()](#new_GLU.this.Shader_new)
    * [.uniformI(name, i)](#GLU.this.Shader.uniformI)
    * [.uniformF(name, f)](#GLU.this.Shader.uniformF)
    * [.uniform2F(name, f1, f2)](#GLU.this.Shader.uniform2F)
    * [.uniform1Fv(name, fvec)](#GLU.this.Shader.uniform1Fv)
    * [.uniform2Fv(name, fvec2)](#GLU.this.Shader.uniform2Fv)
    * [.uniform3F(name, f1, f2, f3)](#GLU.this.Shader.uniform3F)
    * [.uniform3Fv(name, fvec3)](#GLU.this.Shader.uniform3Fv)
    * [.uniform4F(name, f1, f2, f3, f4)](#GLU.this.Shader.uniform4F)
    * [.uniform4Fv(name, fvec4)](#GLU.this.Shader.uniform4Fv)
    * [.uniformMatrix4fv(name, matrixArray16)](#GLU.this.Shader.uniformMatrix4fv)

<a name="new_GLU.this.Shader_new"></a>

#### new this.Shader()
Represents a webGL vertex or fragment shader:

<a name="GLU.this.Shader.uniformI"></a>

#### this.Shader.uniformI(name, i)
Provide an integer (via uniform1i) to the currently bound shader

**Kind**: static method of [<code>this.Shader</code>](#GLU.this.Shader)  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>string</code> | The name of the uniform variable |
| i | <code>number</code> | The integer value |

<a name="GLU.this.Shader.uniformF"></a>

#### this.Shader.uniformF(name, f)
Provide a float (via uniform1f) to the currently bound shader

**Kind**: static method of [<code>this.Shader</code>](#GLU.this.Shader)  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>string</code> | The name of the uniform variable |
| f | <code>number</code> | The float value |

<a name="GLU.this.Shader.uniform2F"></a>

#### this.Shader.uniform2F(name, f1, f2)
Provide a vec2 uniform (via uniform2f) to the currently bound shader

**Kind**: static method of [<code>this.Shader</code>](#GLU.this.Shader)  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>string</code> | The name of the uniform variable |
| f1 | <code>number</code> | The first float value |
| f2 | <code>number</code> | The second float value |

<a name="GLU.this.Shader.uniform1Fv"></a>

#### this.Shader.uniform1Fv(name, fvec)
Provide an array of floats (via uniform1Fv) to the currently bound shader

**Kind**: static method of [<code>this.Shader</code>](#GLU.this.Shader)  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>string</code> | The name of the uniform variable |
| fvec | <code>Float32Array</code> | An array of floats |

<a name="GLU.this.Shader.uniform2Fv"></a>

#### this.Shader.uniform2Fv(name, fvec2)
Provide an array of vec2 (via uniform2fv) to the currently bound shader

**Kind**: static method of [<code>this.Shader</code>](#GLU.this.Shader)  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>string</code> | The name of the uniform variable |
| fvec2 | <code>Float32Array</code> | An array of floats, 2 per vector |

<a name="GLU.this.Shader.uniform3F"></a>

#### this.Shader.uniform3F(name, f1, f2, f3)
Provide a vec3 uniform (via uniform3f) to the currently bound shader

**Kind**: static method of [<code>this.Shader</code>](#GLU.this.Shader)  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>string</code> | The name of the uniform variable |
| f1 | <code>number</code> | The first float value |
| f2 | <code>number</code> | The second float value |
| f3 | <code>number</code> | The third float value |

<a name="GLU.this.Shader.uniform3Fv"></a>

#### this.Shader.uniform3Fv(name, fvec3)
Provide an array of vec3 (via uniform3fv) to the currently bound shader

**Kind**: static method of [<code>this.Shader</code>](#GLU.this.Shader)  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>string</code> | The name of the uniform variable |
| fvec3 | <code>Float32Array</code> | An array of floats, 3 per vector |

<a name="GLU.this.Shader.uniform4F"></a>

#### this.Shader.uniform4F(name, f1, f2, f3, f4)
Provide a vec4 uniform (via uniform4F) to the currently bound shader

**Kind**: static method of [<code>this.Shader</code>](#GLU.this.Shader)  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>string</code> | The name of the uniform variable |
| f1 | <code>number</code> | The first float value |
| f2 | <code>number</code> | The second float value |
| f3 | <code>number</code> | The third float value |
| f4 | <code>number</code> | The fourth float value |

<a name="GLU.this.Shader.uniform4Fv"></a>

#### this.Shader.uniform4Fv(name, fvec4)
Provide an array of vec4 (via uniform4fv) to the currently bound shader

**Kind**: static method of [<code>this.Shader</code>](#GLU.this.Shader)  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>string</code> | The name of the uniform variable |
| fvec4 | <code>Float32Array</code> | An array of floats, 4 per vector |

<a name="GLU.this.Shader.uniformMatrix4fv"></a>

#### this.Shader.uniformMatrix4fv(name, matrixArray16)
Provide a matrix (via uniformMatrix4fv) to the currently bound shader

**Kind**: static method of [<code>this.Shader</code>](#GLU.this.Shader)  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>string</code> | The name of the uniform variable |
| matrixArray16 | <code>Float32Array</code> | An array of 16 floats |

