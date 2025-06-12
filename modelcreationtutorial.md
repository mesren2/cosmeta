# Cosmeta Mod - Creating Custom Cosmetics with Blockbench

Welcome to the comprehensive guide for creating custom cosmetics for the Cosmeta mod using Blockbench! This tutorial will walk you through the entire process of creating 3D models and setting them up for use in Minecraft.

## Table of Contents
1. [Getting Started](#getting-started)
2. [Setting Up Blockbench](#setting-up-blockbench)
3. [Creating Your First Cosmetic](#creating-your-first-cosmetic)
4. [Texturing Your Model](#texturing-your-model)
5. [Exporting for Cosmeta](#exporting-for-cosmeta)
6. [JSON Configuration](#json-configuration)
7. [Advanced Techniques](#advanced-techniques)
8. [Troubleshooting](#troubleshooting)
9. [Examples](#examples)

## Getting Started

### What You'll Need
- **Blockbench** (Free 3D model editor) - Download from [blockbench.net](https://blockbench.net)
- **Image editor** (GIMP, Photoshop, Paint.NET, etc.) for textures
- **Basic understanding** of 3D modeling concepts

### Cosmetic Types
The Cosmeta mod supports four types of cosmetics:
- **HEAD**: Hats, helmets, accessories that attach to the head
- **BODY**: Chest pieces, capes, backpacks
- **LEGS**: Pants, leg armor, decorative leg pieces
- **FEET**: Shoes, boots, foot accessories

## Setting Up Blockbench

### Installation
1. Download Blockbench from the official website
2. Install and launch the application
3. Create a new project: **File > New > Generic Model**

### Initial Setup
1. Set the model format to **Generic Model**
2. Set texture size to **64x64** (recommended for Minecraft compatibility)
3. Name your project (this will be your cosmetic name)

### Workspace Configuration
- **Right Panel**: Outliner (model structure)
- **Center**: 3D viewport
- **Left Panel**: Element properties
- **Bottom**: Timeline (for animations, not needed for static cosmetics)

## Creating Your First Cosmetic

### Basic Model Structure
Let's create a simple hat as an example:

#### Step 1: Planning Your Design
- Sketch your idea on paper first
- Consider the size relative to a Minecraft player (16x16x16 unit head)
- Think about how it will attach to the player

#### Step 2: Creating the Base Shape
1. **Add a cube**: Right-click in Outliner > Add Cube
2. **Position the cube**: 
   - For a hat: Position above the head area
   - X: -4 to 4 (8 units wide)
   - Y: The minecraft player is 32 units tall.
   - Z: -4 to 4 (8 units deep)

#### Step 3: Refining the Shape
1. **Select your cube** in the Outliner
2. **Adjust dimensions** in the Properties panel:
   - Size: Width, Height, Depth
   - Position: X, Y, Z coordinates
   - Rotation: For angled elements

#### Step 4: Adding Details
1. **Duplicate elements**: Ctrl+D
2. **Add more cubes** for details (bands, decorations, etc.)
3. **Use the Move tool** to position elements
4. **Use the Scale tool** to resize elements

### Model Hierarchy
Organize your model in the Outliner:
Hat Model ├── Base Hat ├── Hat Band ├── Feather └── Buckle


## Texturing Your Model

### UV Mapping Basics
1. **Select a cube** you want to texture
2. **Switch to UV Editor**: View > UV Editor
3. **Assign faces** to different parts of the texture

### Creating Textures
1. **Export UV Template**: File > Export > UV Template
2. **Open in image editor** and create your texture
3. **Save as PNG** with the same name as your model

### Texture Guidelines
- **Resolution**: 64x64 pixels (can be higher, but 64x64 is optimal)
- **Format**: PNG with transparency support
- **Style**: Match Minecraft's aesthetic (pixelated, limited colors)
- **Details**: Add shading, highlights, and patterns

### Applying Textures
1. **Import texture**: File > Import > Texture
2. **Select elements** to apply texture to
3. **Use Paint Bucket tool** to apply texture to faces
4. **Adjust UV mapping** if needed in UV Editor

## Exporting for Cosmeta

### Export as OBJ
1. **File > Export > OBJ Model**
2. **Choose export location** (preferably a dedicated folder)
3. **Export settings**:
   - ✅ Include texture coordinates
   - ✅ Export groups
   - ✅ Export materials (if using .mtl files)

### Export Texture
1. **File > Export > Texture**
2. **Save as PNG** in the same folder as your OBJ
3. **Use the same base name** (e.g., `cool_hat.obj` and `cool_hat.png`)

### File Organization
Create a folder structure like this:
My_Cosmetics/ ├── head/ │ ├── cool_hat.obj │ ├── cool_hat.png │ └── cool_hat_config.json ├── body/ │ ├── cape.obj │ └── cape.png └── feet/ ├── boots.obj └── boots.png

## JSON Configuration

### Basic Configuration File
Create a JSON file with the same name as your model:

```json
{
  "scale": 1.0,
  "offset": [0.0, 0.0, 0.0],
  "rotation": [0.0, 0.0, 0.0],
  "attachPoint": "head"
}
```
### Configuration Options
#### Scale
- **Purpose**: Resize the entire model
- **Values**:
    - `1.0` = Normal size
    - `0.5` = Half size
    - `2.0` = Double size

- **Example**: `"scale": 1.2` for a slightly larger hat

#### Offset
- **Purpose**: Move the model's position
- **Format**: `[x, y, z]` in block units
- **Examples**:
    - `[0.0, 0.1, 0.0]` = Move up slightly
    - `[0.0, 0.0, -0.1]` = Move forward slightly

#### Rotation
- **Purpose**: Rotate the model
- **Format**: `[x_rot, y_rot, z_rot]` in degrees
- **Examples**:
    - `[0.0, 45.0, 0.0]` = Rotate 45° around Y-axis
    - `[15.0, 0.0, 0.0]` = Tilt forward 15°

#### Attach Point
- **Purpose**: Specify which body part to attach to
- **Values**: , , , `"head"``"body"``"legs"``"feet"`

### Advanced Configuration Examples
#### Tilted Hat
{
  "scale": 1.1,
  "offset": [0.0, 0.05, 0.0],
  "rotation": [0.0, 0.0, -10.0],
  "attachPoint": "head"
}
#### Floating Crown
``` json
{
  "scale": 1.2,
  "offset": [0.0, 0.5, 0.0],
  "rotation": [0.0, 0.0, 0.0],
  "attachPoint": "head"
}
```
#### Large Cape
``` json
{
  "scale": 1.5,
  "offset": [0.0, 0.0, 0.2],
  "rotation": [0.0, 0.0, 0.0],
  "attachPoint": "body"
}
```
## Advanced Techniques
### Multi-Part Models
Create complex cosmetics by combining multiple elements:
1. **Group related elements** in Blockbench
2. **Export as single OBJ** (Blockbench handles this automatically)
3. **Use hierarchy** for better organization

### Animation Considerations
While Cosmeta doesn't support animations yet, prepare for future updates:
1. **Name bones consistently** (head_bone, body_bone, etc.)
2. **Keep pivot points logical** (center of rotation)
3. **Organize hierarchy** properly

### Optimization Tips
1. **Keep polygon count low** (< 100 faces for simple cosmetics)
2. **Use minimal texture resolution** needed
3. **Combine similar elements** where possible
4. **Remove unnecessary faces** (inside faces, etc.)

### Blockbench Shortcuts
- **G**: Move tool
- **S**: Scale tool
- **R**: Rotate tool
- **Ctrl+D**: Duplicate
- **Tab**: Switch between Edit and Paint modes
- **Alt+Mouse**: Orbit camera
- **Scroll**: Zoom camera

## Troubleshooting
### Common Issues
#### Model Not Appearing
- **Check file names**: OBJ and PNG must have same base name
- **Verify file format**: Must be valid OBJ and PNG files
- **Check texture size**: Very large textures may cause issues

#### Model Too Big/Small
- **Adjust scale** in JSON config
- **Check Blockbench units**: 1 unit = 1 pixel in Minecraft
- **Compare to player model**: Head is 8x8x8 units

#### Texture Not Loading
- **Check texture path**: Must be in same folder as OBJ
- **Verify PNG format**: Must be valid PNG with proper transparency
- **Check UV mapping**: Ensure faces are properly mapped

#### Model Positioning Issues
- **Adjust offset** in JSON config
- **Check pivot point** in Blockbench
- **Verify attach point** setting

### Debugging Steps
1. **Test with simple model** first (single cube)
2. **Check console logs** for error messages
3. **Verify file permissions** (read access)
4. **Try different texture sizes** (32x32, 64x64, 128x128)

## Examples
### Example 1: Simple Top Hat
#### Blockbench Setup
1. Create base cylinder: 6x6x4 units
2. Add hat brim: 10x10x1 units
3. Position brim at bottom of cylinder
4. Add hat band: 6.5x6.5x0.5 units

#### Texture (64x64 PNG)
- Black base color (#000000)
- Dark gray shading (#333333)
- Red hat band (#AA0000)
- Metallic buckle (#FFD700)

#### Configuration (top_hat_config.json)
``` json
{
  "scale": 1.0,
  "offset": [0.0, 0.0, 0.0],
  "rotation": [0.0, 0.0, 0.0],
  "attachPoint": "head"
}
```
### Example 2: Angel Wings
#### Blockbench Setup
1. Create wing frame: Thin rectangles for main structure
2. Add feather details: Small cubes for individual feathers
3. Mirror for second wing
4. Group both wings

#### Configuration (angel_wings_config.json)
``` json
{
  "scale": 1.3,
  "offset": [0.0, 0.2, 0.3],
  "rotation": [0.0, 0.0, 0.0],
  "attachPoint": "body"
}
```
### Example 3: Rocket Boots
#### Blockbench Setup
1. Create boot base: 4x6x8 units each
2. Add thruster details: Cylinders at back
3. Add flame effects: Colored transparent cubes
4. Duplicate for second boot

#### Configuration (rocket_boots_config.json)
``` json
{
  "scale": 1.1,
  "offset": [0.0, 0.0, 0.0],
  "rotation": [0.0, 0.0, 0.0],
  "attachPoint": "feet"
}
```
## Tips for Great Cosmetics
### Design Principles
1. **Keep it Minecraft-style**: Blocky, pixelated aesthetic
2. **Consider proportions**: Don't make cosmetics too large
3. **Think about gameplay**: Avoid blocking player vision
4. **Be creative but practical**: Cool designs that work in-game

### Color Schemes
1. **Use limited palettes**: 3-5 main colors work best
2. **Consider contrast**: Dark and light areas for definition
3. **Match Minecraft colors**: Look at existing items for inspiration
4. **Add gradients carefully**: Use dithering for smooth transitions

### Testing Your Cosmetics
1. **Test on different skins**: Various player models
2. **Check in different lighting**: Day, night, underground
3. **Test movement**: Walking, running, jumping
4. **Verify with other cosmetics**: Ensure they don't conflict

## Conclusion
Creating custom cosmetics for Cosmeta is a fun and creative process! With Blockbench and these guidelines, you can create amazing accessories for your Minecraft character. Remember to:
- Start simple and build complexity gradually
- Test frequently during development
- Share your creations with the community
- Have fun and be creative!

## Resources
### Download Links
- [Blockbench](https://blockbench.net) - Free 3D model editor
- [GIMP](https://www.gimp.org) - Free image editor
- [Paint.NET](https://www.getpaint.net) - Free Windows image editor
``` 
## Additional Tutorial Files

<llm-snippet-file>cosmeta/tutorials/examples/simple_hat_config.json</llm-snippet-file>
```
json { "scale": 1.0, "offset": [0.0, 0.0, 0.0], "rotation": [0.0, 0.0, 0.0], "attachPoint": "head", "description": "A simple hat example", "author": "Tutorial", "version": "1.0" }
``` 

<llm-snippet-file>cosmeta/tutorials/examples/advanced_wings_config.json</llm-snippet-file>
```
json { "scale": 1.2, "offset": [0.0, 0.3, 0.4], "rotation": [10.0, 0.0, 0.0], "attachPoint": "body", "description": "Advanced wing cosmetic with custom positioning", "author": "Tutorial", "version": "1.0", "advanced": { "renderPriority": 1, "transparency": 0.9, "glowEffect": false } }
``` 

<llm-snippet-file>cosmeta/tutorials/quick_start.md</llm-snippet-file>
```
markdown
# Quick Start Guide - Cosmeta Cosmetics
## 5-Minute Setup
### 1. Download Blockbench
- Go to [blockbench.net](https://blockbench.net)
- Download and install

### 2. Create Your First Model
1. Open Blockbench
2. File > New > Generic Model
3. Add a cube (Right-click > Add Cube)
4. Resize it to 8x4x8 units
5. Position it above the origin (Y: 0-4)

### 3. Add a Simple Texture
1. Create a 64x64 PNG image with your favorite colors
2. In Blockbench: File > Import > Texture
3. Select your PNG file
4. Use the Paint Bucket tool to apply texture to cube faces

### 4. Export Your Model
1. File > Export > OBJ Model
2. Save as "my_first_hat.obj"
3. File > Export > Texture
4. Save as "my_first_hat.png" in the same folder

### 5. Create Configuration
Create a file named "my_first_hat_config.json":
``` json
{
  "scale": 1.0,
  "offset": [0.0, 0.0, 0.0],
  "rotation": [0.0, 0.0, 0.0],
  "attachPoint": "head"
}
```
### 6. Upload to Cosmeta
1. Open Minecraft with Cosmeta mod
2. Go to Cosmetics screen
3. Click "Upload Custom"
4. Select your OBJ file for model
5. Select your PNG file for texture
6. Enter a name and upload!

## Next Steps
- Read the full README.md for detailed instructions
- Experiment with different shapes and textures
- Try creating body, legs, or feet cosmetics
- Share your creations with the community!
``` 

This comprehensive update includes:

1. **Updated CustomCosmeticUploadScreen** with separate model and texture file uploads
2. **Detailed instructions** for OBJ and JSON model support
3. **Complete Blockbench tutorial** covering everything from basics to advanced techniques
4. **JSON configuration examples** for different cosmetic types
5. **Troubleshooting guide** for common issues
6. **Quick start guide** for beginners
7. **Example configuration files** for reference

The tutorial covers all aspects of creating custom cosmetics, from initial design to final implementation, making it easy for users to create their own unique cosmetics for the mod.
```
