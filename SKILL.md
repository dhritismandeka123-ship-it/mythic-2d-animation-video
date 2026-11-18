---
name: mythic-2d-animation-video
description: Makes a cinematic 2560x1440, 60 fps MP4 mythology film from the user's voiceover, script and 2 reference videos, with everything animated (characters, world, camera). Use for any mythology, epic or legend video. All rules are inside this skill.
---

# MYTHIC CINEMATIC ANIMATION VIDEO SKILL (v4)

The user uploads this file once into the skill section. Per video the user only attaches: ORIGINAL VOICEOVER AUDIO + COMPLETE SCRIPT + REFERENCE VIDEO 1 + REFERENCE VIDEO 2 (and optionally reference images of characters), and writes one short line such as "Use the Mythic skill and make the video." Everything else is defined here and must be followed automatically, without the user pasting any master prompt.

---------------------------------------------------------------------

## 0. READ THIS FIRST: MISSION, THE FAILURES TO NEVER REPEAT, AND THE HARD GATES

READ ORDER: read this Section 0 first. Then read Sections 22, 23 and 24 (they are at the end of this file: the animation engine, the motion proof, and the framing proof) BEFORE writing any code. Then read the rest.

MISSION: turn the voiceover and script into a finished, immersive, Hollywood-quality mythology film in which EVERYTHING IS ANIMATED: every character, every strand of hair and fold of cloth, every ornament, every tree, leaf, blade of grass, cloud, wave, flame, wisp of smoke, bird, butterfly, raindrop and ray of light, and also the camera. The viewer must feel they are inside a living world, not watching pictures slide past. Write real code, run it, render it, deliver the finished MP4.

You act simultaneously as: film director, cinematographer, virtual-camera engineer, character designer, rigger and animator, environment artist, simulation/VFX artist, lighting artist, film composer, sound designer, mixing engineer and render engineer. Make every creative decision yourself; do not ask the user questions unless a required input is missing or unreadable.

### THE TWO FAILURES THAT RUINED THE LAST VIDEOS (fix both, prove both)

FAILURE 1: ONLY THE CAMERA MOVED. This is the worst failure. In the last video the camera flew around, but the characters, environments, trees, clouds, water, creatures and everything else were still pictures. A camera moving over still pictures is NOT animation and is NOT acceptable. The user asked for everything to be animated. The camera is only ONE of six animation layers, and it is the LEAST important of them. If the camera were frozen, the film must still look alive.

FAILURE 2: CHARACTERS LEFT THE FRAME OR WERE CUT IN HALF. The camera drifted so far that characters went out of the picture. Framing must be guaranteed BY CONSTRUCTION in the render loop (a runtime clamp, Section 24), not hoped for.

### THE SIX ANIMATION LAYERS (all must be active in every shot; the camera is only layer 6)
1. CHARACTER BODY AND FACE: breathing, weight shifts, blinks, gaze, head motion, hands, and a real action for what the narration says (walk, pray, speak, draw a bow, point, bow, ride, fight).
2. CHARACTER SECONDARY MOTION: hair, beard, cloth, pallu, cape, garlands, feathers, earrings, jewellery, all driven by physics and wind.
3. ENVIRONMENT: trees, leaves, grass, flowers, water, fire, smoke, mist, clouds, banners, hanging cloth.
4. LIFE AND WEATHER: birds, butterflies, flies, insects, animals, fireflies, rain, snow, dust, falling leaves and petals, lightning.
5. LIGHT: flickering flames and their light on faces, moving god-rays, dappled light through leaves, cloud shadows, changing time of day, glints on ornaments.
6. CAMERA: eased, smooth, motivated movement (Section 11).
Every shot must visibly move in at least four of layers 1-5 even if the camera is perfectly still. This is tested (Gate A).

### NON-NEGOTIABLE RULES (all always)
1. EVERYTHING ANIMATES (layers 1-6 above). Camera-only motion over still images is a failed video.
2. REAL MP4, 2560x1440 (2K QHD), TRUE 60 fps, H.264/AVC, yuv420p, AAC 48 kHz, playable on Android. This has been tested and confirmed possible in this environment. Do not downgrade, do not ask permission to downgrade, do not substitute WebM / HTML / GIF / image sequences, do not rename a WebM to MP4, do not duplicate frames to fake 60 fps. If a time limit interrupts rendering, continue in chunks (Section 3) until the full film is finished and joined. Verify the real file with ffprobe before delivering.
3. The ORIGINAL VOICEOVER is used exactly as uploaded: never regenerated, re-voiced, sped up, slowed down, pitch-shifted, time-stretched, trimmed, filtered, noise-reduced or compressed. It is the source of truth for timing. No narration line may be omitted or reordered.
4. NO on-screen text of any kind (no subtitles, captions, titles, chapter cards, lower thirds, quotes, logos, watermarks, channel names).
5. FRAMING: a character is never out of frame or cut off (except a deliberate, flagged extreme close-up). Guaranteed by the runtime clamp (Section 24).
6. CAMERA: dynamic and cinematic: fast and dramatic when the scene demands it, calm when the scene is calm, SMOOTH ALWAYS (Section 11).
7. CHARACTERS ARE DETAILED AND SCRIPT-ACCURATE, with physics-driven hair, cloth and jewellery (Sections 6 and 7).
8. THE WORLD IS REAL AND LIVING: time of day, weather, wind, plants, animals, insects, water, fire and light behave like the real world (Section 9).
9. ENVIRONMENT CONTINUITY: each new place is built uniquely; a place that returns later is the SAME place (Section 8).
10. MUSIC AND SOUND EFFECTS ARE MANDATORY: calm and gentle by default, changing with the scene, professionally mixed (Sections 13-15).
11. COMPLETE DELIVERY: all narration, all scenes, finished MP4 + ORIGINAL_VOICEOVER.m4a + SOURCE_PROJECT.zip. Never stop after the plan, a preview, or code only.
12. NEVER save render time by freezing things. If compute-limited, reduce the resolution of the motion fields or the particle counts; never replace animation with a still image.

### THE FIVE HARD GATES (you may not deliver, and may not claim success, until all five pass; show a compact GATE REPORT table in chat)
- GATE A: ANIMATION PROOF (Section 23). Test clips rendered with the CAMERA LOCKED must show measured, visible motion in characters, environment and sky, in every location and for every hero character.
- GATE B: FRAMING PROOF (Section 24). framing_log.json for every frame shows zero violations, with the runtime clamp active, plus a contact sheet inspected.
- GATE C: AUDIO PROOF. The voiceover in the final MP4 is sample-identical in content, order, speed and pitch to the original; music and SFX present; ducking verified; no clipping.
- GATE D: EXPORT PROOF. ffprobe confirms MP4, h264, 2560x1440, 60 fps, yuv420p, AAC 48 kHz, correct duration, A/V sync at start, middle and end.
- GATE E: TEXT-FREE PROOF. Sample frames contain no text.
If a gate fails, fix the cause and run it again. Do not lower a threshold to pass. If a gate still cannot pass after real attempts, say exactly which one and why, in two plain lines, and deliver the best verified result.

HONESTY RULE: only claim what was actually produced and verified.

---------------------------------------------------------------------

## 1. INPUTS AND PRIORITY ORDER

Inputs: (1) original voiceover audio, (2) complete script, (3) reference video 1, (4) reference video 2, (5) optional character/location reference images or descriptions.

If any input is missing or unreadable, name it in one line and continue with what exists.

PRIORITY WHEN RULES CONFLICT:
1. The original voiceover and the script's facts (what is said, when, who, where).
2. The user's attached references (videos, images, written descriptions): they define the exact look of the art, characters and mood and override the default look in this file wherever they clearly differ.
3. This skill file.
4. Your own creative judgement (use it freely wherever the above are silent; the user explicitly wants you to add camera sequences, weather, wildlife and other cinematic touches wherever they suit the story).

Reverent tone: this is mythology told with respect. Serious, documentary-like, emotional, cinematic. Never comic, never mocking, never a cartoon.

---------------------------------------------------------------------

## 2. PRODUCTION WORKFLOW (follow in order, do not stop early)

PHASE 1: INSPECT. Check the audio (duration, sample rate, channels), both reference videos (resolution, fps, duration; sample frames), and the script. Inspect the sandbox (Section 3.1).

PHASE 2: STUDY THE REFERENCES. Analyse both reference videos: character designs, proportions, faces, costume detail; background art; palette and colour grade; lighting, glow, shadow, depth; composition and placement; animation smoothness; camera angles and moves; transitions; pacing; particles and environment motion; overall mood. Reproduce their visual language, then raise the detail, depth, motion and camera quality as this skill describes. Do not produce a generic AI slideshow.

PHASE 3: ANALYSE VOICEOVER + SCRIPT.
- Get the real audio duration. If the script has timestamps, use them. Otherwise detect speech with silence/energy analysis and align sentences to the audio (cumulative word count, about 0.25 s pause at sentence ends, snapped to detected pauses). Expose a global OFFSET value for sync nudging.
- Split into visual beats of about 3-8 s, always on meaningful narration units. Every scene must show exactly what is being narrated at that moment.
- Extract the STORY TIMELINE (morning, noon, evening, night, days later, years later, weather events, seasons) because it drives the lighting and weather (Section 9).

PHASE 4: CAST SHEET (Section 6). One detailed character card for every character, deity, animal, creature, army and key object. Cards never change after creation.

PHASE 5: LOCATION BIBLE (Section 8). One entry per place with a spatial layout. Build each new place uniquely; reuse returning places exactly.

PHASE 6: STORYBOARD + CAMERA CHOREOGRAPHY. A timestamped table with columns: Beat #, start-end, narration snippet (short), location id, time-of-day/weather, characters + script action verbs mapped to animation clips (Section 22.9), shot code, camera energy (1-5), camera path summary, WHY this move (story reason), transition-out, music cue, SFX cues. Plan the camera energy curve (Section 11.7).

PHASE 7: AUDIO PLAN. Music sections with key/mode and instruments, plus the SFX cue sheet with timestamps (Sections 13-14).

PHASE 8: BUILD. Write the engine and the data files (Section 3.3) following the animation engine in Section 22 (build and test in the order of 22.8); generate layered, animation-ready assets; run the camera pre-pass (Section 11.2m); pass GATE A (animation proof, Section 23) and GATE B (framing proof, Section 24) before any full render, and fix every failure.

PHASE 9: RENDER in chunks, in parallel where possible, with checkpoint/resume (Section 3.5). Never skip or reduce animation to save render time.

PHASE 10: MIX AND ENCODE. Synthesise or assemble music and SFX, mix with the untouched voiceover, mux with the video, encode (Section 3.6, 15).

PHASE 11: VERIFY (Section 18) and DELIVER (Section 17).

CHAT OUTPUT: keep chat messages short. Show the cast sheet (compact), the location list, the storyboard table (compact), the GATE REPORT table (Gates A-E), then the finished files and the verified specs. Do not paste large code into chat unless asked; the code goes into SOURCE_PROJECT.zip.

---------------------------------------------------------------------

## 3. RENDER ENGINEERING (how to code this at a professional level)

### 3.1 Inspect the sandbox first
Check ffmpeg/ffprobe, Python version, installed libraries (numpy, scipy, Pillow, opencv, pycairo, skia-python, moderngl/EGL, moviepy, soundfile, librosa), CPU core count, RAM, disk, and any execution time limit. Pick the fastest working stack. Run a 3-second benchmark render at full 2560x1440, 60 fps to measure seconds-per-frame and plan chunk sizes. If a GPU/OpenGL context is available, use it for compositing; otherwise use numpy/OpenCV on CPU with multiprocessing.

### 3.2 Architecture principles
- ANIMATION BEFORE CAMERA: every frame first animates the world and the characters for time t (Section 22.1), then evaluates the camera and the runtime framing clamp (Section 24), then composites. Never build a pipeline that only moves a camera over still images.
- DETERMINISTIC TIME: every frame n is computed from t = n / 60.0 exactly. All animation, simulation and camera values are pure functions of t (plus fixed seeds). No state that accumulates drift. This makes chunked and parallel rendering seamless: any chunk can start at any frame and produce identical results.
- SEPARATE DATA FROM ENGINE: a new video = new data files, not new engine code.
  - cast.json (character cards), locations.json (location bible), storyboard.json (beats, shots, camera keyframes, transitions), weather_timeline.json, audio_cues.json (music sections + SFX cues), wind.json parameters.
- ONE GLOBAL SIMULATION CLOCK: wind, weather, water, fire, creature paths and particles keep running on the global clock regardless of cuts or camera moves, so the world never "resets" when the camera arrives.
- RESOLUTION-AWARE QUALITY: extreme close-ups must be razor sharp. Either draw vector paths directly each frame with the camera's transform (best), or pre-rasterise every sprite at multiple levels of detail (1x, 2x, 4x) and pick the level from its on-screen scale. Never blow up a low-resolution bitmap.
- SUB-PIXEL EXACTNESS: all transforms in floating point with bicubic/Lanczos or bilinear resampling and proper antialiasing. Never round positions to whole pixels (this is the main cause of shimmer and "not smooth" motion).
- PRE-RENDER STATIC LAYERS (far sky, distant mountains, static ground textures) once and reuse; re-render only what changes.

### 3.3 Modules to implement
1. math: vectors, matrices, quaternions/look-at, Catmull-Rom and B-spline paths with arc-length parameterisation, easing functions (cubic, quintic, smootherstep, cubic-bezier), spring/critically-damped smoothers, seeded noise (simplex/Perlin).
2. camera: rig (position, target, roll, FOV, focus distance, aperture), keyframe evaluator, subject-lock framing solver, safe-frame validator, motion blur sampler.
3. world: location prefabs, billboard/slice objects, ground plane, sky dome, cylindrical world ring for 360-degree views, fog, depth sorting.
4. characters: part-based rig, view sets for turning, face system, ornaments, physics (hair/cloth/jewellery), pose and action library (Section 7).
5. living_world: time-of-day lookup, weather, wind field, clouds, rain, lightning, flora motion, fauna agents, water, fire, particles (Section 9).
6. lighting_fx: key/fill/rim, dynamic lights, shadows, god-rays, bloom, flares, colour grade, grain, vignette (Section 10).
7. audio: music synthesis/assembly, SFX synthesis/assembly, cue scheduler, ducking, mixer, limiter (Sections 13-15).
8. render: chunk scheduler, parallel workers, encoder pipes, checkpoint/resume, concatenation, mux, ffprobe verification.
9. validate: camera framing validator, edge-coverage validator, text-free check, A/V sync check, contact-sheet generator.

### 3.4 Layered 2.5D scene model (true perspective camera)
- Every location is a small 3D stage: a ground plane, a sky dome, and objects placed at real (x, y, z) world positions. Trees, huts, pillars, rocks, banners, props, characters and creatures are camera-facing sprites or stacked-slice objects with a pivot on the ground.
- Project every object with a real perspective camera: for a world point P, camera position C and rotation R (from look-at plus roll), Pc = R^T (P - C); screen x = cx + f * Pc.x / Pc.z; screen y = cy - f * Pc.y / Pc.z; where f = (H/2) / tan(FOV_vertical / 2). Sprite scale = f / Pc.z. Sort back to front by Pc.z. Clip against a near plane (about 0.3 units). Apply depth fog with exp(-density * z).
- VIEW-DEPENDENT OBJECTS: every prop and tree has at least a SIDE view and a TOP view; blend them by camera pitch (0 to 90 degrees) so drone and top-down shots show proper canopy circles, rooftops and layouts rather than squashed side views. Large buildings and rocks get 3-5 stacked slices at different depths so orbits reveal volume.
- 360-DEGREE SUPPORT: environments are built as a ring around the focal area (landmarks at world coordinates in all directions) so an orbit around a character reveals a consistent surrounding world, not a flat backdrop.
- CHARACTERS IN 3D SPACE: a character stands at a world position and has a facing angle. Compute the view angle between the facing direction and the camera, and use the character's turntable view set (Section 7.1) so orbits and passes feel like real turning.
- Do NOT convert characters into realistic 3D models. Keep the illustrated art style and achieve the 3D feeling with perspective, parallax, turntable cut-outs, stacked slices, lighting and camera motion.

### 3.5 Chunked, parallel, resumable rendering
- Split the timeline into chunks of about 5-10 s. Render chunks in parallel worker processes (one per CPU core), each piping frames to its own ffmpeg process with IDENTICAL x264 settings (fixed GOP, for example keyint=120:min-keyint=120:scenecut=0) so chunks join with `-c copy` without re-encoding.
- Save each finished chunk to disk immediately (checkpoint). If a time limit interrupts, resume from the first missing chunk; never restart from zero and never lower quality.
- Log progress (chunk number, fps achieved, estimated time left). Keep going until all chunks exist, then concatenate.
- Use motion-blur sub-sampling (3-8 sub-frames) only on frames where on-screen motion exceeds about 12 px per frame, to save time.

### 3.6 Encoding and audio muxing (reference commands, adapt as needed)
Per chunk (video only):
ffmpeg -y -f rawvideo -pix_fmt rgb24 -s 2560x1440 -r 60 -i - -c:v libx264 -preset slow -crf 16 -maxrate 35M -bufsize 70M -profile:v high -level 5.2 -pix_fmt yuv420p -x264-params keyint=120:min-keyint=120:scenecut=0 -r 60 chunk_0001.mp4
Concatenate and mux the final mixed audio:
ffmpeg -y -f concat -safe 0 -i chunks.txt -i final_mix.wav -map 0:v -map 1:a -c:v copy -c:a aac -b:a 256k -ar 48000 -movflags +faststart COMPLETE_FINAL_VIDEO.mp4
Target video bitrate 20-35 Mbps. Verify:
ffprobe -v error -show_entries stream=codec_name,width,height,r_frame_rate,pix_fmt,sample_rate,duration -of default=nw=1 COMPLETE_FINAL_VIDEO.mp4
Expect h264, 2560, 1440, 60/1, yuv420p, aac, 48000, and a video duration equal to the voiceover duration plus a calm tail of at most about 3 s.
ORIGINAL_VOICEOVER.m4a: if the source is already AAC/M4A use `-c copy`; otherwise encode once at high quality (AAC 256 kbps or higher) or deliver the source file as is.

---------------------------------------------------------------------

## 4. VISUAL IDENTITY AND ART DIRECTION

QUALITY BAR: a premium animated mythology feature film. Rich, painterly, ornate illustration with real depth, light and atmosphere. Not a children's cartoon, not anime/manga, not pixel art, not photographic, not a flat paper slideshow.

STYLE DEFINITION ("illustrated realism"):
- Layered vector/painterly illustration with soft multi-tone shading (base, shadow, highlight, rim), fine ornament detail, fabric folds and patterns, expressive faces. Detail comes from drawing (ornaments, folds, textures, light) and motion, not from photoreal rendering or 3D models.
- Colour, character proportions, and mood follow the user's reference videos first. Where the references are simpler than this description, still add the detail level required here without changing the reference's palette, proportions or identity.
- Backgrounds are rich painted worlds with many depth layers, atmosphere and life. Frames always have a clear light source and depth cues (fog, haze, bokeh foreground, rim light).
- Edges: soft, clean, antialiased. Thick black cartoon outlines are not used; a thin warm rim-light edge appears where a light source grazes a character (stronger at night/dusk).
- Violence is never graphic: show it with silhouettes, arrow streaks, fire, smoke, red skies, dust and sound. No gore, blood or dismemberment.

DETAIL BUDGET (minimum, per hero character, so close-ups hold up): face 25+ shapes (eyes with iris, pupil, highlight, lids, lashes, brows, nose, lips, cheeks, jaw shading, ear), costume 20+ shapes with fold lines and border patterns, 8+ separate ornament pieces, hair in 15+ strands/locks or ribbon shapes. Supporting characters: about half that. Crowd members: simplified but still shaded silhouettes.

POST-PROCESSING ON EVERY SHOT (final pass, in this order): depth-of-field, motion blur (when moving fast), bloom/glow, lens flare (subtle, only with strong lights), atmospheric haze, colour grade, vignette, light film grain. See Section 10.

## 5. COLOUR PALETTES (approximate hex, use as the base)

General: dark umber #1b140d, deep brown #3a2a1c, parchment #e8d9b5, antique gold #d9a441, bright gold glow #ffd37a, saffron/orange #d9772b, maroon #6b1f26, crimson glow #c0262d, sage green #6b7a4f, forest green #2e4a2a, leaf green (lit) #4f9a34, night indigo #231f45, dusk purple #3a2d5c, storm slate #3b4a5e, mist grey #9aa3a8, mauve cloud #8a6a7a, sunset coral #c9714f, cream cloud #f3dfb8, moon #e9e6d8.

Per environment:
- Lanka at dusk: teal-navy sky #1e2c40 -> #0e1624, gold spires #d9a441 with warm window dots #ffcf70.
- Lanka at sunset: orange-amber sky #e8863a -> purple #3a2d5c, buildings amber-brown #a8702a.
- Forest ashram: sage/olive greens only (desaturated), light shafts pale yellow-green.
- Storm / hilltop: slate blue, mauve, pink-coral cloud highlights.
- Library of scrolls: all brown #2a1d12 with a single warm lamp light.
- Ashoka grove (night): indigo + purple, dark green trees with small red/orange blossom dots, red rim light on characters.
- Battlefield: smoky grey-brown, orange fire dots, crimson sky glow when violence peaks.
- For stories outside these examples, derive new environment palettes in the same family: earthy muted tones, warm gold glows, teal/slate shadows, one clear light source. Time of day and weather (Section 9) shift these palettes smoothly.

---------------------------------------------------------------------

## 6. CHARACTERS: DESIGN, DETAIL AND SCRIPT-ACCURACY

### 6.1 Character card (build for EVERY character before drawing anything; never change it afterwards)
Fields: id; name; role (hero, villain, deity, sage, king, queen, warrior, woman, child, animal, giant, crowd); age look (child, young, adult, elder); body build and height multiplier (1.0 human, 0.5-0.7 child, 1.5-3.0 giant); skin base/shadow/highlight hex; face (Section 6.2); hair (style, colour, length, ties); headgear (crown/mukut, jata, helmet, turban, feather); beard/moustache; upper garment, lower garment, shawl/cape/sash (colour, fabric, border pattern); jewellery list with materials and positions; signature weapon/prop (with details); distinctive far-away silhouette feature; aura/halo (colour, shape); rim-light colour for dusk/night (orange-gold for most, red for villains, blue-white for deities); default pose; idle motion; expression set; costume states (Section 6.3); voice/behaviour notes that affect posture (calm, proud, humble, fierce).

### 6.2 Face system (faces must be expressive and detailed, never blank dots)
- Eyes: almond or lotus-shaped sclera, iris with a darker ring, pupil, a small specular highlight that moves with the key light, upper lid shadow, lashes, optional kajal line. Eyebrows with shape that carries expression. Nose with bridge highlight and nostril shading. Lips with a light highlight and a gentle default curve. Cheek and jaw shading from the key light. Ears with ornaments. Forehead markings (tilak, tripundra, bindi, third eye) exactly as the iconography says.
- Expression set per character (neutral, calm/serene, stern, angry, sorrow, joy/smile, shock, devotion, determination). Expressions are built from brow angle, eyelid openness, eye direction, lip curve and slight cheek lift. Change expression smoothly (0.3-0.6 s) to match the narration's emotion.
- No lip-sync (narration-led film), but faces are never frozen (Section 7.4).
- Extreme close-ups must show real detail: eyelashes, iris pattern, tilak texture, jewellery glints, skin shading, wind in the hair.

### 6.3 Costume, ornaments and story-accurate states
- Costume details: fabric type (silk with sheen, cotton matte, leather, bark, deer-skin), border embroidery, fold lines in a darker tone, a lit-side highlight, hems that move.
- Ornament pieces (as the character requires): crown or mukut with gems and pearl strings, kundal/earrings, necklaces (haar), garlands (vaijayanti mala, flower garlands), armlets (bajuband), bracelets (kangan), waist belt (kamarband), anklets (payal), rings, toe rings, nose stud, maang tikka, hair ornaments, kavach/armour plates. Each is its own part with its own physics (dangle, swing, glint).
- COSTUME STATES: derive from the script. The same character changes costume only when the story changes it (royal court, exile in bark cloth and matted hair, battle armour, mourning, disguise, divine form). Each state is a defined variant of the card; use the correct one per scene and keep it consistent within that stretch of story.
- If the user gives a reference image or description, follow it over the defaults below.

### 6.4 Iconography library (accurate defaults; adapt to the script and references)
Draw with reverence and accuracy. Colours are guides; follow the Section 5 palettes.

RAMAYANA
- SRI RAM: serene, composed, noble; deep blue-green/dark blue complexion (neel kamal tone, #4c7fb0 day, #2f4a7a darker scenes), long lotus eyes, gentle half-smile, broad shoulders and long arms, upright poise. Royal state: tall ornate gold mukut with gems, vertical tilak, gold kundal, pearl and gold necklaces with a pendant, flower garland, armlets, bracelets, yellow silk dhoti with gold border, red-orange uttariya, Kodanda bow (golden, curved) and quiver with fletched arrows. Exile state: matted hair in a high jata topknot, ochre/bark-cloth garment, minimal jewellery, same calm face. A faint blue-white halo in sacred moments.
- LAKSHMAN: fair golden-brown skin, athletic, fierce loyal eyes, tilak, simpler crown or jata in exile, red sash, bow and quiver, stands slightly behind Ram.
- SITA / MAA SITA: golden-fair, graceful, long black hair (braid or loose), sindoor in the parting, red bindi, maang tikka, jhumka earrings, gold necklaces, bangles, saree in red/yellow with a flowing pallu; exile state in a simple saffron/ochre saree; in Ashoka Vatika a plain yellow saree, tired but dignified.
- HANUMAN: powerful vanara with saffron-orange/golden-red fur look, expressive red-brown face, gold kundal, mala, tilak, red/yellow loincloth, gada (mace), long tail, flies horizontally with trailing cloth; huge form when the script says so.
- RAVAN: dark charcoal-indigo skin, ten heads in an arc (central head larger and higher), each with a tall pointed golden crown with a red gem, black beards, white tilak lines, maroon dhoti, red-maroon cape, gold armlets, curved sword (Chandrahas) or mace; very broad; red-orange rim light.
- KUMBHAKARNA and GIANTS: gigantic, dark brown skin, tusks, spiked crown, long black hair, black cross-sash, huge spear; low-angle shots with a tiny army below.
- MEGHNAD / INDRAJIT, VIBHISHAN, JATAYU (large vulture), SAMPATI, SUGRIV, VALI, JAMBAVAN (grey bear), ANGAD, DASHARATH, KAUSHALYA, KAIKEYI, BHARAT, VASHISHTHA, VISHWAMITRA: build from the archetypes with distinctive silhouette features.
- PARSHURAM: warm tan-brown skin, long black matted hair in a high topknot, full black beard, rudraksha necklace, saffron-orange dhoti, cross-body strap, orange-yellow shawl, parashu (axe with silver crescent blade) on a long shaft.

KRISHNA STORIES / MAHABHARAT
- SRI KRISHNA: dark blue-black "shyam" complexion with a soft luminous sheen, youthful, large lotus-shaped eyes, a gentle knowing smile, curly dark locks framing the face, gold mukut with a peacock feather (mor pankh) and pearl strings, vertical tilak, makar kundal, vaijayanti mala (long flower garland) with pearl and gold necklaces and the Kaustubha gem, yellow pitambar silk dhoti with gold border, uttariya blowing in the wind, bajuband, kangan, kamarband, anklets, bansuri flute (gold-banded). Child Krishna (Bal Gopal): small, round face, curls, tiny peacock feather, tiny flute, anklets, butter pot, cows and gopas around. Kurukshetra Krishna: charioteer in royal yellow, reins in hand, Sudarshan chakra on the finger when invoked, calm eyes amid chaos.
- RADHA / GOPIS: fair to golden skin, long dark hair with flowers, colourful lehenga-choli or saree (blue, pink, yellow), ornate jewellery.
- ARJUN: warm brown skin, strong focused face, Gandiva bow, twin quivers, simple gold crown/helmet, blue-white sash. KARNA: golden kavach and kundal, sun-glow aura. BHISHMA: white hair and beard, white cloth, grand and grave; the bed of arrows. DRONA: white hair, saffron robe, bow. DURYODHAN: maroon royal clothes, gold crown, mace. DUSHASAN, SHAKUNI (grey hair, dice), YUDHISHTHIR (calm, simple crown), BHIMA (massive, mace), NAKUL, SAHADEV, DRAUPADI (dark-complexioned, long open black hair, red saree, rich jewellery), KUNTI, GANDHARI (blindfold), DHRITARASHTRA, ABHIMANYU (young warrior), GHATOTKACH, SANJAY.

DEITIES AND PURANAS
- VISHNU: blue skin, four arms holding Sudarshan chakra (golden disc), Panchajanya conch (white), Kaumodaki mace, padma (lotus); tall golden kirita crown, yellow pitambar, Kaustubha gem and Srivatsa mark, vanamala garland, big golden halo; reclining on the multi-hooded Shesha in the cosmic ocean, or floating in clouds.
- LAKSHMI: golden-fair, red/pink saree, gold jewellery, seated on a pink lotus, two elephants pouring water, gold coins. BRAHMA: orange-tan, four faces (three visible), white beards, small crowns, on a pink lotus, with Vedas, kamandalu, rosary and a swan. SARASWATI: white saree, veena, white lotus, swan.
- SHIVA: ash-white skin with a blue-tinged throat (Neelkanth), three horizontal ash lines (tripundra) and a vertical third eye, matted jata topknot with the Ganga stream and a crescent moon, cobra around the neck, rudraksha malas, tiger-skin wrap, trishul with damaru, Nandi the bull nearby, a calm meditative face. PARVATI: golden-fair, red saree, crown, sindoor, rich jewellery. GANESHA: elephant head with one tusk, large ears, round belly, orange-red body, modak, small mouse. KARTIKEYA: youthful, peacock, vel spear.
- DURGA: golden-saffron skin, 8-10 arms with weapons (trishul, chakra, conch, bow, sword, mace, lotus), red saree, gold crown, rides a lion. KALI: dark blue-black skin, many arms, wide eyes, red tongue accent, stylised garland (no gore). HANUMAN, GARUDA (golden eagle-man with wings), SHESHA (white multi-hooded serpent), NANDI.
- INDRA: gold crown, vajra (thunderbolt), white elephant Airavat. SURYA: blazing golden disc halo, chariot with seven horses. CHANDRA: pale, silver glow. YAMA: dark skin, noose and danda, buffalo. VARUN: sea-blue, waves. AGNI: flame-red aura. NARAD: sage with veena, tilak, white-saffron clothes.
- VISHNU AVATARS: Matsya (golden fish), Kurma (tortoise), Varaha (boar), Narasimha (lion-man, golden mane, fierce), Vamana (small Brahmin with umbrella), Parshuram, Ram, Krishna, Kalki (white horse). Keep Vishnu's blue-gold cues.
- SAGES / RISHIS: long white or grey beard, matted hair or bald, white/ochre cloth, rudraksha beads, kamandal, seated in meditation beside a small fire, calm powerful presence.
- Other mythologies (if the script asks): use correct iconography in the same style (Zeus with lightning, Odin with one eye and ravens, Anubis with a jackal head, etc.).
- NEW CHARACTERS not listed: invent them with the same detail rules: one signature prop, one far-away silhouette feature, skin and costume colours from the palette, full face and ornament set.

### 6.5 Archetype templates
- DEITY: calm upright poise, halo/aura behind the head, heavy jewellery, symmetrical multi-arm fan if needed, floats on clouds/lotus, soft glow pulse, blue-white or gold rim light.
- KING / EMPEROR: tall ornate crown, cape/sash, broad stance, weapon at side, court or army background.
- WARRIOR / HERO: armour plates or cross-strap, weapon in hand, confident stance, hilltop back-view shots.
- SAGE: white/grey beard, plain cloth, rudraksha, kamandal, seated meditation, small fire.
- DEMON / RAKSHASA / ASURA: dark indigo-grey or dark brown skin, tusks or horns, spiked crown, heavy build, red/orange rim light; extra heads/arms if the story says so.
- QUEEN / WOMAN: long hair, bindi, earrings, saree with a long flowing end, graceful poised movement.
- CHILD: smaller (0.5-0.7), rounder face, bigger eyes, simpler clothes, lively movement.
- ANIMAL / BIRD / CREATURE: anatomically believable silhouettes with proper gait or wingbeat cycles; one accent colour (golden fish, vulture, white elephant, lion, hooded serpent, bull, peacock, garuda, deer, cow, horse).
- GIANT: size 2-3x, low-angle shot, tiny army in the foreground.
- CROWD / ARMY: Section 7.11.

### 6.6 Consistency rules
- Same id = same look in every scene (face, colours, ornaments, proportions). Changes only through defined costume states.
- Never draw readable text on clothes or props.
- Lighting may tint a character (warm sunset, cold moonlight, firelight) but the base colours stay the same.
- Keep the physical scale between characters consistent (a child stays smaller than adults; a giant stays a giant).

---------------------------------------------------------------------

## 7. CHARACTER ANIMATION (must look like real movement)

### 7.1 Rig and turntable
- Build every character from separate parts with real joints: head (with separate hair layers, crown, ornaments), neck, torso (chest/abdomen), pelvis, upper arm / forearm / hand (with fingers or a few finger groups for gestures and holding), thigh / shin / foot, plus cloth, shawl, garlands, jewellery, weapon. Rotate parts around true joint pivots with proper parent-child chains (shoulder drives elbow drives wrist).
- TURNTABLE VIEW SET: each hero character has FRONT, THREE-QUARTER, SIDE and BACK variants of face/torso art (mirrored for left/right). Use a continuous yaw value; shift parts horizontally by their local depth (x' = x*cos(yaw) + z_part*sin(yaw)), squeeze widths by |cos(yaw)| (minimum about 0.35), and cross-fade between view variants at the thresholds over about 0.15 s so orbits read as real turns.
- Keep a contact shadow under every standing character (soft ellipse that follows the feet) plus a cast shadow whose direction and length follow the sun/moon/fire.

### 7.2 Motion principles (apply to everything)
- Use the classic principles: anticipation before an action, follow-through after, overlapping action (parts lag each other), arcs (limbs move on curved paths), slow-in/slow-out, secondary action, weight and balance (hips and shoulders counter-rotate, weight shifts between feet).
- All timings below are defaults at 60 fps; scale to the narration's mood. Calm scenes use slow, smooth, dignified motion. Nothing snaps, pops or teleports; nothing bounces like a cartoon.
- Every character is ALWAYS moving gently: breathing (chest/shoulders rise 1-2 %, 3-4 s period), micro weight shifts every 4-8 s, blinks every 3-6 s (0.12-0.18 s), tiny head and gaze motion, cloth and hair responding to wind. Random phase per character.

### 7.3 Secondary physics (hair, cloth, jewellery) driven by the global wind
- Model hair locks, beard, shawl ends, saree pallu, capes, garlands, crown feathers (peacock feather), tassels, earrings and necklaces as chains/ribbons of segments with spring-damper or verlet physics: each segment follows its parent with stiffness, damping and gravity, and is pushed by the wind field (Section 9.3) and by the character's own acceleration.
- Characters' hair is NEVER frozen: when there is any wind it streams and ripples; in still air it still drifts slightly; during fast motion it trails behind; after a stop it settles with a small overshoot.
- Cloth hems and sleeves ripple with a travelling wave (phase along the length), amplitude from wind speed. Dangling jewellery swings with a pendulum motion (period 0.6-1.2 s, decaying). Ornaments glint when the key light angle passes (short bright sparkle, 0.1-0.2 s).
- Garlands sway and lag behind torso motion; peacock feathers flutter with a gentle double-frequency wobble.

### 7.4 Face and eye animation
- Blink cycle (Section 7.2), eye saccades and gaze targets (look at the speaker's subject, at the horizon, at another character), eyelid and brow changes with emotion, slight head tilt and turn (5-12 degrees) as thought moves, breathing visible in shoulders and throat. Eyes lead head turns by about 0.1-0.2 s. Pupils react subtly to bright light.
- Hold expressions with micro-movement (very small brow and lid shifts) so close-ups feel alive.

### 7.5 Locomotion
- WALK: full cycle (contact, down, passing, up) about 1.0-1.1 s per stride for an adult; torso bob 2-3 % of height; hips and shoulders counter-rotate; arms swing opposite to legs (smaller for dignified or armed characters); cloth drags and flutters; feet plant with no sliding (match foot speed to ground speed); dust or grass reacts at the feet; toes and heels roll correctly.
- RUN: stride about 0.5-0.6 s, forward lean, bigger arm swing, hair and cloth streaming back, short airborne phase.
- STAND/SIT/KNEEL/BOW transitions: 0.8-1.4 s with weight shifting and hand support, no sudden pose swaps.
- RIDING: chariot wheels rotate in proportion to speed, horses use a believable gallop cycle with head bob, manes and tails streaming, chariot body bounces slightly on the road and dust trails behind; riders brace with knees and sway with the motion.
- FLYING / LEVITATING: horizontal or upright body with a slow vertical sine drift (8-15 px equivalent), trailing cloth, aura and particles.
- Characters walking through grass, water, mist or dust disturb them (blades bend, ripples spread, dust puffs).

### 7.6 Gestures and mudras
Namaskar (folded hands, slight head bow), abhaya mudra (raised open palm, blessing), pointing, beckoning, embracing, lifting, carrying (weight shown in the carrier's posture), giving or receiving objects, grief (hands to face, slumped shoulders), anger (clenched fists, rigid posture), devotion (kneeling, forehead to the ground), thinking (hand at chin). Hands are drawn with proper finger shapes and move with eased arcs.

### 7.7 ARCHERY (dhanush): smooth, powerful, believable (use this exact phase plan)
Bow geometry: the bow is a curved limb (Bezier) whose curvature depends on a draw value d from 0 to 1; the string is two segments meeting at the nocked point that moves back with d. Limbs bend more as d rises. The arrow has a shaft, an arrowhead, and feathered fletching.
1. STANCE (0.4-0.6 s): feet about shoulder-width apart, body side-on to the target, weight settled, eyes lock on the target; cloth settles.
2. NOCK (0.5-0.7 s): the draw hand reaches back over the shoulder to the quiver, takes an arrow (small tug), brings it forward, places it on the string; the bow hand holds the bow steady.
3. RAISE (0.4-0.6 s): the bow arm rises and extends toward the target with a slight shoulder rotation and chest opening; anticipation (tiny dip) before the rise.
4. DRAW (0.7-1.0 s, ease-in-out): the draw hand pulls the string back to the anchor point (cheek/ear), the draw elbow rises and swings back in line with the arrow, shoulder blades pinch, the chest expands, the string forms a V, bow limbs bend with draw d = 0 to 1, a slight tremble builds in the arms, jaw tightens, hair and cloth pulled back by the effort.
5. AIM/HOLD (0.3-0.6 s): minimal tremor (about 0.5 px equivalent), breath held, narrowed eyes, a tiny settle.
6. RELEASE (frames, not seconds): fingers open and the string snaps forward in 1-2 frames; the draw hand recoils back and slightly down; bow limbs spring forward and oscillate with decaying vibration (3-4 cycles over about 0.4 s); the string vibrates as a damped sine; a quick air ripple and tiny muzzle-like burst of dust/leaf particles from the string side.
7. ARROW FLIGHT: the arrow accelerates instantly, travels on a slight parabola with a small fishtail wobble, shaft rotating subtly, a thin glowing trail and a sound whoosh with a Doppler-like pitch shift; for divine astras add colour-coded glow, particles and light on the surroundings (fire, water, wind, lightning variants).
8. FOLLOW-THROUGH (0.4-0.8 s): bow arm holds the line, eyes track the arrow, cloth and hair whip forward then settle, shoulders relax slowly.
9. IMPACT: the arrow embeds with a small puff of dust/sparks, brief camera micro-shake on heavy hits only, target reaction.
- VOLLEY / RAPID FIRE: reload cadence about 0.3-0.4 s; arrows fly in arcs with slight spread; many silhouettes falling or fading with smoke (never gore).
- ARROW-CAM (optional hero shot): the camera rides behind or alongside a flying arrow through the environment (Section 11.6).

### 7.8 Other weapons and combat
- SWORD/AXE/MACE: wind-up (anticipation, 0.3-0.5 s), fast arc swing (0.15-0.3 s) with a motion trail, contact with a small spark/dust burst, recovery (0.3-0.5 s). Heavy weapons show weight (slower, bigger body rotation, ground reaction).
- SHIELD, SPEAR, CHAKRA (spinning disc with trail and light), TRIDENT, GADA duels: believable spacing, footwork, blocks and sparks. Fights are cinematic and readable, never frantic noise.
- Big impact beats: very short camera shake (4-6 px for 0.2-0.3 s) plus dust shockwave and a light flash.

### 7.9 Divine and supernatural motion
Appear/disappear with golden-white light bursts and particles dissolving upward; levitation; aura pulses; multiple arms fanning with staggered phase; halo rotation; transformation into giant/divine forms with scale and light build-up; astra summoning with swirling energy; boons shown as a line of sparkles between giver and receiver; sacred fire and smoke.

### 7.10 Animals and creatures
- Birds: flap cycles with wing folds, glide phases, banking. Horses and deer: correct gaits. Cows and elephants: slow heavy walk with swaying trunk/tail. Monkeys: agile arcs. Serpents: sinusoidal body wave with a swaying hood. Fish: tail wave. Lions: shoulder roll and tail flick. Peacocks: tail fan shimmer. Garuda and Jatayu: huge slow wingbeats with wind pushing on the environment.
- Each has idle behaviour (ear flicks, tail swish, head turns, breathing).

### 7.11 Crowds and armies
Each member has its own phase, height and speed variation so nothing moves in lockstep; rows march with natural stride, raised weapons sway, banners ripple in the wind, dust rises from feet; depth gradient (smaller, hazier, bluer toward the back). Use instanced rendering for performance, with 3-4 costume variants. Battle crowds fall/fade with smoke, never gore.

### 7.12 AMBIENT MOTION FLOOR (anti-still rule, applies to every scene; measured in Section 23)
Every shot contains the idle layer for every visible character (breathing, weight shift, blinks, gaze, micro head motion, hair, cloth, jewellery), at least one narrative action clip per character per beat (Section 22.9), and living motion in the environment, weather, creatures and light. Every frame must contain at least 8 independent gentle motions, spread over at least four of the five non-camera animation layers, with the minimum visible amplitudes in Section 23.1. Amplitudes are small and smooth, so calm scenes feel alive and peaceful, never still, and never frantic.

---------------------------------------------------------------------

## 8. LOCATIONS: UNIQUE PER SCENE, IDENTICAL ON REVISIT

### 8.1 Location bible (build before animating)
For every place in the script create an entry: id; name; purpose in the story; TOP-DOWN LAYOUT with world coordinates for every landmark (for example hut at (-6, 2), banyan at (4, 7), pond at (0, -5), gate at (0, 20)); ground type; horizon and sky; key props; light sources; ambient life (Section 9.11); default time of day and weather; named camera vantage points (front view, side view, aerial view, doorway view); and a fixed random seed. Every camera angle in that place is computed from this one layout, so every view of the place is geometrically consistent.

### 8.2 Every new scene gets a NEW, unique, richly built environment
- For each new place, invent and code a distinct environment that fits the script: unique landmark arrangement, vegetation mix, architecture, colour accents (within the palettes), props and atmosphere. Two different places must never look like recolours of each other.
- Build each environment with at least 6 depth layers plus world-ring objects (Section 3.4), at least 5 different prop types, a distinct skyline/horizon, foreground framing elements (branches, pillars, rocks, grass blades, banners) and background life.
- Use a procedural toolkit with seeded variation: tree species (banyan, peepal, neem, mango, palm, bamboo, pine, sal), canopies and trunks with branch structure, rocks, grass tufts, flowers, lotus ponds, huts (thatched roof, dark doorway), pillars with carved bands, arches, domes and spires, balustrades, steps, gates, walls, banners, lamps, ghats, boats, bridges, carts, cave mouths, cliffs, snow peaks, clouds.

### 8.3 Revisit rule (very important)
If the story returns to a place it has already shown (for example: home, then school, then back home), the place is the SAME place:
- Reuse the same location entry, layout, seed, object positions, proportions and colours. A returning viewer must recognise it instantly.
- Only these may differ: time of day and weather/lighting, the characters present, the camera angle (shown consistently from the same layout), and story-driven changes that the narration states (burned, flooded, rebuilt, decorated, years later, season changed). Apply such changes on top of the SAME layout (for example the same hut, now charred).
- Do not rebuild a visited place with a different arrangement, and do not reuse a different place's layout for a new place.
- Keep a registry in locations.json: location id -> first appearance time, all later appearances, and any story-driven state changes.

### 8.4 Base environment library (starting designs; extend or adapt, keep the same quality bar)
Build each from layered depth objects (Section 3.4). These designs came from the user's original reference videos.

1. LANKA (night version): dark navy sky with a pale moon, a long island platform with a horizontal balustrade railing in the foreground, many golden stepped-pyramid spires (tall, tapering, each with a lit tip) in a dense skyline. Water/horizon line low. Ravan stands in front, huge.
2. LANKA (sunset version): amber sky, sea horizon with glitter, dark rocky hill behind the city, round-domed gold towers, fortress gate with a dotted door, stepped spires. Armies stand in a dense row in front.
3. FOREST ASHRAM: layered sage/olive "lollipop" trees (round canopies on thin trunks) in 3 depths, two small thatched huts with dark doorways on left and right, a small campfire, pale diagonal god-rays through the trees, dark framing tree silhouettes at the left/right edges, soft dust floating.
4. STORM CLOUDS / HILLTOP: wide painterly cloud bands (slate, mauve, coral edges), a dark rocky hilltop in the foreground where the hero stands (seen from behind), tiny distant trees or temple silhouettes, sometimes a green globe/moon in the sky.
5. SCRIPTURE LIBRARY: dark brown wall of shelf grid, brown floor, one small oil lamp (diya) at the lower right with a flame glow; cream parchment scrolls (rounded rectangles with two small dark holes) slide in horizontally and stack vertically, filled with unreadable decorative ancient-script glyphs (decorative only, not real readable text).
6. PALACE HALL: maroon-brown wall, three tall arched blue windows, gold pillars, two small flame torches at the bottom corners, a central figure framed in the middle arch with a halo.
7. ASHOKA GROVE (night): indigo sky with stormy purple clouds and a big white moon, castle wall with arched windows at left, dense dark-green trees with orange/red blossom dots, glowing gold picket fence in the distance, tiny flame on the ground near the seated Sita, red blossom petals on the ground.
8. SKY WITH CHARIOT: sunset sky, huge fluffy cream clouds in 3 layers moving at different speeds, bright sun glow behind, flying chariot drifting slowly across.
9. BURNED BATTLEFIELD: grey haze, towering ruined temple silhouettes, small orange fires on the ground, dark broken ground, smoke.
10. OPEN BATTLE PLAIN WITH FOREST EDGE: green tree line, golden grass, a rock outcrop in the foreground where Ram/Sita/Lakshman stand; sky changes from blue-teal -> orange -> deep crimson as the battle escalates; destroyed army shown as a dark textured heap with small fires and smoke.
11. DARK MURAL GALLERY (for reflective/closing moments): dark stone wall with recessed arched niches and framed panels lit by candles at the bottom; golden mural silhouettes of earlier scenes appear inside the niches; camera pans slowly sideways along the wall.
12. VOID / SYMBOL BACKGROUNDS: dark brown blank background with floating dust and a single glowing symbol (sundial, lotus, three diyas, a clock-like shape, a fish with a boat) for abstract or time-related narration; soft beige radial glow for "divine/blinding light" moments.
13. THEATER STAGE (for "a play" references): red curtains on both sides, a painted forest backdrop, little foot-lights.

### 8.5 Additional environments to draw from
Village lane and mud-brick home with courtyard, tulsi plant and cows; home interior with oil lamps; gurukul/school with trees and a teaching platform; river ghat with steps and boats; riverbank at dawn; cave with torchlit walls; Himalayan snow peaks and Mount Kailash; the cosmic ocean (Kshirsagar) with Shesha; heavens (Swarg) with golden palaces on clouds; underworld (Patal) with glowing gems and dark caverns; royal court (sabha) with carved pillars and throne; temple with lamps, bells and a spire; royal road and city street with market stalls; farmland with crops in wind; desert with dunes and heat shimmer; mountain pass; sea shore with waves; swayamvar hall; yagna (sacred fire) ground; Kurukshetra plain with chariots and banners; burning city; flooded land; starry night sky and moonlit meadow.

---------------------------------------------------------------------

## 9. THE LIVING WORLD (real-world behaviour in every scene)

Everything here runs on the global simulation clock (Section 3.2), is driven by the story timeline, and keeps running while the camera moves. The goal is that the viewer feels a real world, not a painted backdrop.

### 9.1 Time of day (follow the story timeline)
- Phases: pre-dawn, sunrise, morning, noon, afternoon, golden hour, sunset, dusk, night (moonlit or dark), deep night. The script's cues ("that evening", "at midnight", "next morning", "years later") set the phase.
- Each phase defines: sky gradient (top, mid, horizon colours), sun or moon position, light colour/temperature (cool blue pre-dawn, warm gold sunrise, neutral-white noon, deep gold-orange golden hour, magenta-purple dusk, blue-indigo night), ambient light level, shadow direction (opposite the sun) and length (about height / tan(elevation)), fog colour, star visibility, and the colour grade.
- Transitions between phases are CONTINUOUS and slow (tens of seconds across scenes): the sky gradient blends, the sun slides down, shadows lengthen, lamps and windows light up, stars fade in. Never a sudden pop.
- Night: moon with a soft halo and passing clouds, twinkling stars, cool moonlight as the key, warm golden sources (diyas, torches, campfires, windows) as contrast, rim light on characters, fireflies (Section 9.5), owls and crickets.
- Storm/darkness: when the story needs "darkness", "storm", "doom", the sky darkens progressively, contrast rises and colour drains toward slate and indigo.

### 9.2 Weather
- States: clear, scattered clouds, overcast, mist/fog, drizzle, heavy rain, thunderstorm, dust storm, snow, heat haze. Weather changes build gradually and are motivated by the story.
- CLOUDS: 3-5 layers with different speeds (far slow, near faster), soft billowing edges lit from the sun side (bright rim, darker underside), slow shape morphing (scale pulse 1.00-1.03 and edge drift), parallax during camera moves, correct colour per time of day. Storm clouds are heavy, dark slate/purple with rolling motion and a bright backlit rim.
- RAIN: thin streaks in 3 depth layers (far: short, faint, slow; near: long, bright, fast; foreground bokeh drops), slanted by the wind direction and strength (30-45 degrees in gusts), with splashes on the ground, ripples on water, drops running on surfaces, wet-ground sheen and reflections, dripping from leaves and roofs, and mist near the ground. Rain intensity ramps up and down smoothly. Rain also darkens colours slightly and adds a cool tint.
- LIGHTNING (rare, dramatic): a sudden flash (0.08-0.25 s, sometimes a double flicker) that lights the whole scene with cold blue-white light, long hard shadows, a visible branching bolt only occasionally, and a fading afterglow. Thunder arrives AFTER the flash (delay 0.5-3 s) in the audio.
- STORM SEQUENCE: calm, then wind rises, then clouds darken and speed up, then first drops, then rain, then gusts, flashes and thunder; trees thrash, leaves fly, cloth and hair whip, flames lean or flicker out. After the storm: rain thins, clouds break, light rays burst through, wet surfaces sparkle, leaves drip, mist rises, a rainbow when it suits the story.
- FOG/MIST: depth-based, drifting banks, light shafts through mist; breath fog in cold.
- DUST STORM/HEAT HAZE/SNOW: particle layers with wind direction, soft density changes, shimmer distortion over hot ground, falling snow with varied flake sizes.

### 9.3 One global wind field (drives everything coherently)
Define wind(x, z, t) = baseDirection * (baseSpeed + gustAmplitude * noise(x * kx + z * kz - t * sp, t * st)), with slow and fast noise components so there are calm moments, steady breezes and gusts that travel across the scene. Wind direction and strength come from the weather state. The SAME wind value drives: tree canopies and branches, individual leaf flutter and falling leaves, grass and crops, flowers, bamboo, flags and banners, characters' hair/beards/cloth/garlands/feathers, smoke and flame lean, dust and petals, cloud drift speed, rain slant, water ripples, and the wind sound level. Gusts visibly sweep across the scene from one side to the other.

### 9.4 Plants
- Trees: trunk sways minimally, branches sway more, leaf clusters flutter at higher frequency with phase offsets per cluster; canopy sway about 0.5-2 degrees (more in wind) with periods of 4-6 s plus fast leaf shimmer. Leaves fall and spin down; petals drift. Foreground trees move slightly more and opposite to the camera drift.
- Grass and crops ripple in travelling waves; flowers nod; bamboo bends in gusts; lotus leaves rock on water with ripples around them; vines and hanging roots swing.
- Dappled light: light patches moving through foliage across the ground and characters, animated with the canopy motion.

### 9.5 Animals and insects (always some life, matched to place and time)
- DAY: flocks and single birds crossing the sky (V formations, circling kites/eagles, crows, parrots, sparrows in bushes, peacocks on the ground), with believable wing cycles and banking; butterflies with erratic fluttering paths (fast flap, wandering drift, brief landings on flowers); bees and flies as small buzzing dots with looping paths; dragonflies that hover and dart; squirrels, deer, cows, monkeys in suitable scenes; fish jumping and frogs near water; swans, cranes, ducks on ponds.
- DUSK: bats streaming out, birds returning to trees, insects swarming in the light.
- NIGHT: owls, moths circling lamps and torches, soft crickets (sound), and FIREFLIES.
- FIREFLIES (night grove, riverbank, forest, farmland at dusk/night): 40-200 per scene depending on the shot; warm golden-yellow glow (#ffd36b to #ffe28a core with a soft, larger additive halo about 6-14 px at 2560x1440); each blinks on its own rhythm (smooth rise 0.2-0.4 s, hold about 0.2 s, fall 0.4-0.8 s, off 1-3 s, individual phase); each drifts slowly along a noise-based wandering path (about 10-40 px/s) with gentle vertical bobbing; denser near water, bushes and tall grass; they appear gradually as darkness grows and fade toward dawn; nearby leaves receive a faint warm tint; near-camera fireflies become soft bokeh orbs for depth. Pair them with warm golden-yellow lamp and fire light against the cool moonlight.
- Creatures obey depth, scale and perspective; foreground insects and leaves pass near the lens as soft out-of-focus accents; no creature ever intersects characters or objects.

### 9.6 Water
Rivers flow with directional ripples and foam at stones; ponds show soft concentric ripples and sky/character reflections (mirrored and slightly distorted); the sea has layered swell, sparkles at the horizon and foamy shore waves; waterfalls have mist and spray; boats rock and leave wakes; rain makes ripple rings; stepping into water makes splashes.

### 9.7 Fire and artificial light
Flames flicker (scale 0.9-1.1, noise-driven at 6-12 Hz), lean with the wind, throw sparks and embers that rise with wobble, and give off smoke that drifts and expands (3-5 s life). Fire light flickers on nearby surfaces and faces (colour temperature about 1800-2200 K, intensity noise), casting moving shadows. Diyas, torches, campfires, yagna fires, burning cities and lamps all do this. Heat shimmer distorts the air above large fires.

### 9.8 Atmosphere
Floating dust motes and pollen catching the light, moving god-rays (pulsing 0.12-0.30 opacity over 6-8 s with slow sideways drift), haze and depth fog (far layers lighter and bluer), drifting mist banks, dew glints on leaves, smoke trails, falling petals, cloud shadows moving across the ground.

### 9.9 Life density guide (minimum living elements per environment)
- FOREST (day): canopy sway, falling leaves, dappled light, birds, butterflies, dust motes, god-rays, small animals, grass sway, drifting clouds.
- NIGHT GROVE: moonlit canopy sway, fireflies, owl or bat, drifting mist, flickering torch or lamp, twinkling stars, passing clouds, warm/cool light contrast.
- VILLAGE/HOME: smoke from chimney or hearth, hens and cows, hanging cloth in wind, children or villagers moving, birds, flickering diya at dusk.
- PALACE/COURT: torch flicker, banners rippling, attendants with slow ambient motion, light shafts from windows, drifting incense smoke, pigeons or parrots outside.
- RIVER/POND: flowing water, reflections, lotus motion, cranes or swans, dragonflies, mist.
- BATTLEFIELD: dust, smoke columns, fires, banners, drifting embers, crows overhead, crimson or stormy sky, army motion.
- MOUNTAIN/SKY/HEAVENS: layered moving clouds, snow spray, eagles, golden light rays, floating divine particles.
- SEA: swell, sparkles, gulls, wind spray, passing clouds.

### 9.10 Linking audio to the simulation
Derive sound levels from the same simulation (wind sound gain follows the wind value, rain sound follows rain intensity, thunder follows the lightning flash time, fire crackle follows flame size, wings follow bird passes). See Section 14.

---------------------------------------------------------------------

## 10. LIGHTING, VFX AND POST-PROCESSING

- LIGHT MODEL: every scene has a key light (sun, moon, fire, divine glow), a sky fill (colour of the sky), and rim lights. Characters are relit per scene: tint by the ambient colour, shade by the key direction, rim in the specified rim colour. Soft contact shadows and directional cast shadows on the ground.
- VOLUMETRIC-STYLE LIGHT: animated god-rays through foliage and windows, light shafts in mist and incense, soft divine glow, warm bloom around bright sources, subtle halation, tasteful lens flare only for strong lights.
- DEPTH: depth fog, atmospheric perspective (far = lighter, bluer, lower contrast), depth of field with background and foreground blur by distance from the focus plane, rack focus between subjects when the camera hands off, foreground bokeh elements (leaves, grass, insects, rain drops).
- MOTION BLUR: 180-degree shutter equivalent on fast camera moves and fast actions; none on slow moves.
- REFLECTIONS AND SPECULARS: ornament glints, metal and weapon highlights, wet ground sheen, water reflections.
- COLOUR GRADE: filmic S-curve, slightly desaturated earthy tones, teal/slate shadows with orange/gold highlights; adapt per mood while keeping one consistent film look.
- FILM LOOK: light animated grain (3-5 %), vignette (centre transparent to about 0.45-0.55 at corners), subtle halation, a clear light source in every frame and darker edges.
- MOOD PRESETS: DIVINE (golden or blue-white light, stronger bloom, slowly rotating faint rays, floating light particles); PEACE (soft green-gold daylight, gentle rays, birds, butterflies); SUSPENSE (deep shadows, narrow key, low haze, slow drifting fog); BATTLE (smoke, fire glow, crimson or stormy sky, silhouettes, embers); SORROW (desaturated cool light, slow rain or mist, low sun); STORM (slate and indigo, high contrast, flashes); CLOSING (calm warm light, slow settle, fade to black).
- PARTICLES: dust, pollen, embers, sparks, smoke, rain, snow, petals, fireflies, magical sparkles, divine light motes, each with seeded randomness and wind influence.

---------------------------------------------------------------------

## 11. THE VIRTUAL CAMERA SYSTEM (animation layer 6: powerful, but never a substitute for animating characters and the world)

IMPORTANT: the camera is only the sixth animation layer. A camera moving over still pictures is a failed video (Section 0). The characters and the world are animated first (Sections 7, 9, 22, 23) and the camera then travels through that moving world.

GOAL: a Hollywood-style, FPV-drone-inspired 3D camera that travels through the world: extreme close-ups of faces, objects and environment details; fast, dramatic travelling shots from one character to another; pull-backs that reveal the whole environment; 360-degree orbits; drone and top-down aerial views; whole loops such as character -> environment -> object -> aerial view. It is used where the scene demands it or where your cinematic judgement says it will make the film better, and it is calm where the story is calm. The camera is fast when it should be fast and SMOOTH ALWAYS. The world keeps animating the whole time (Section 11.10).

### 11.1 Camera model
- A true virtual camera inside the 3D stage (Section 3.4): position, look-at target, roll, vertical FOV, focus distance and aperture, all keyframed on splines (Catmull-Rom or B-spline with arc-length parameterisation) and evaluated per frame from t = n / 60.
- Compute framing distance from the subject size: to make a subject of height h fill a fraction q of the frame height at vertical FOV theta, place the camera at d = h / (2 * q * tan(theta / 2)). Use this for every shot, orbit radius and pull-back so framing is exact and not guessed.
- Each shot in storyboard.json is defined by: id, start/end time, SUBJECT SET (the must-show actors/objects), CROP INTENT (FULL, WAIST-UP, CHEST-UP, FACE, ECU), shot code, camera keyframes, easing profile, focus plan, transition-out.

### 11.2 FRAMING GUARANTEES (mandatory; enforced by code on every frame, see Section 24)
In the previous videos the camera swung so far that characters left the frame or were half cut off. Hoping the camera path is right is not enough: framing is enforced by a runtime clamp in the render loop on EVERY frame, and the camera planning also follows these rules.
a. DEFAULT = THE WHOLE SUBJECT IS VISIBLE. Every shot declares a SUBJECT SET (the must-show actors/objects) and a CROP INTENT (FULL is the default; WAIST-UP, CHEST-UP, FACE and ECU only when chosen on purpose). A partially cropped subject is allowed ONLY in flagged close-ups, and then the crop falls on natural cut points (never through an eye, never a half-visible face when the shot is about the face; an ECU of a face shows both eyes and brow fully).
b. SAFE FRAME: for FULL and WAIST-UP shots, the projected bounding box of every must-show subject (including crown, hair top, raised weapon, feet and lowest garment hem) stays inside the safe frame (5 % margin on all sides) in 100 % of frames. The only exception is a flagged hand-off where one subject deliberately exits while the next enters.
c. HEADROOM AND FOOTROOM: in medium and close shots, the top of the head (including the crown) sits 6-12 % below the top edge; in full shots leave 5-10 % below the feet. Leave look-room (10-15 %) in the direction the subject faces or moves.
d. PITCH LIMITS: outside AERIAL shots, camera pitch stays within +/-30 degrees. Moving up or down (crane, rise, dive) is done by moving the camera position in world space while the look-at target keeps following the subject's body, so the subject stays framed and merely changes size. Never tilt the camera away from the subject to point at sky or ground.
e. AERIAL/TOP-DOWN: pitch may go up to 90 degrees ONLY in shots flagged AERIAL. The subject then stays inside the central 60 % of the frame and is at least 3.5 % of the frame height (still clearly visible as a small figure), unless the shot is explicitly handing over to another subject.
f. SUBJECT-LOCK CONTROLLER: the look-at target is the weighted centre of the must-show bounding box, followed by a critically damped spring (x'' = w^2 * (target - x) - 2 * w * x', with w about 6-10 rad/s) with a small dead-zone for micro-motion, plus lead toward the subject's motion. Framing never jitters.
g. HAND-OFFS (character A to character B): move the focus target along an eased spline from A to B, and keep at least one of them (or the travel path) in frame the whole time; arrive with B placed on a rule-of-thirds line with look-room.
h. ORBITS: radius computed with the framing formula (11.1) so the subject's silhouette stays inside the safe frame at every angle; orbit centre = the subject's chest/waist; pitch stays within +/-10 degrees.
i. WALK/RUN TRACKING: lead the subject by 10-15 % of frame width; camera lag at most about 0.4 s; the camera never overtakes the subject. CHARACTERS NEVER WALK OR MOVE OUT OF FRAME BY THEMSELVES: plan the characters' world motion together with the camera so they stay inside the region the camera covers, unless the narration says they leave (then flag a deliberate exit).
j. NO EMPTY EDGES: every layer (sky dome, ground plane, world ring, fog) extends beyond the largest camera extents, so no black, blank or unpainted area ever shows (except a planned fade). Run a coverage test.
k. RUNTIME CLAMP (the guarantee): after the camera path is evaluated for frame n and BEFORE that frame is rendered, run fit_camera() (Section 24). It projects the full bounding box of every must-show subject in its CURRENT pose (crown, hair top, raised weapon, feet, hem) and, if any part leaves the safe frame, re-centres the camera and dollies it back until everything fits. The clamp ALWAYS wins over any camera keyframe. Smooth the correction so it never causes a visible jerk; the planning pass should already make runtime corrections close to zero.
l. LOGGING AND GATE B: write framing_log.json (per frame: subject boxes, margins, correction applied). After rendering, GATE B (Section 24) checks every frame: zero violations, plus an inspected contact sheet.
m. PRE-PASS: before the real render, evaluate the full camera path at 60 fps and test every frame for (1) subjects inside the safe frame, (2) no empty edges, (3) pitch and roll limits, (4) velocity/acceleration continuity and speed limits (Section 11.3), (5) no NaN or sudden jumps. Auto-fix every violation (increase the camera distance with the formula in 11.1, move the target, reduce pitch, lengthen the move) and repeat until there are none.

### 11.3 SMOOTHNESS STANDARDS (fast but never jerky)
- Position and look-at paths are C2-continuous (velocity AND acceleration continuous); never switch abruptly between linear segments. Use quintic ease or cubic-bezier speed profiles: normal moves cubic-bezier(0.65, 0, 0.35, 1); whips and dives cubic-bezier(0.76, 0, 0.24, 1) (slow start, strong peak, long soft settle). No linear speed, no bounce, no overshoot-and-snap-back.
- SPEED RAMPS: accelerate for at least 0.25-0.5 s, peak, then decelerate for at least 0.5-1.0 s into the final composition (the settle is what makes it feel professional).
- Angular speed limits: normal moves at most about 60 degrees/s; whips up to about 220 degrees/s ONLY under heavy motion blur and only for 0.2-0.4 s; roll (banking) at most about 6 degrees and only in turns, eased in and out.
- Always render with sub-pixel exactness, antialiasing, and true 60 fps (each frame evaluated at t = n/60). No frame holds, no integer snapping, no timing hitches.
- MOTION BLUR (180-degree shutter equivalent) on fast moves using 4-8 sub-frames; none on slow moves. The blur hides cuts, sells speed and removes stutter.
- Layers should be separated in depth so nearer layers sweep faster than far ones (strong, convincing parallax) at every speed.
- Micro-drift: even in a calm held shot, the camera has a very slow breathing drift (0.5-1.5 % scale or position) so the frame is never perfectly frozen. No constant handheld shake; shake only for heavy impacts (4-6 px for 0.2-0.3 s).

### 11.4 TIMING GUIDE (defaults at 60 fps; adjust to the narration)
- Extreme close-up hold: 0.8-1.6 s (with slow push or micro-drift).
- Fast hand-off whip between subjects: 0.9-1.6 s.
- Pull-back reveal (close-up to wide): 2.0-3.5 s; to full aerial: 3-5 s.
- Gentle glide/track: 3-6 s.
- Orbit: 90 degrees in 3-5 s, 180 degrees in 5-8 s, 360 degrees in 8-14 s.
- Dive from high to subject: 2.0-3.5 s. Rise/crane up to aerial: 2.5-4.5 s.
- Low FPV weave through objects: 2-4 s.
- Whole loop sequences (11.6): 12-24 s.
- Calm held composition for peaceful/emotional narration: 6-12 s with gentle drift and lots of ambient life.

### 11.5 SHOT DICTIONARY (use these codes in the storyboard)
Shot sizes: ECU-F (extreme close-up: eyes, face), ECU-O (object macro: arrow tip, flute, crown, diya flame, jewel, scroll, weapon edge), ECU-E (environment macro: dew drop, flame, ripple, butterfly on a flower, wind in leaves, rain on water), CU, MCU, MS, WS (wide), EWS (extreme wide/establishing), plus angle tags LA (low angle, heroic/menacing), HA (high angle), AER (aerial), TOP (top-down).
Camera moves:
- PUSH / DRIFT / PULL: slow push-in, pull-out and gentle drift for calm beats (energy 1-2).
- PB (PULL-BACK REVEAL): start on an extreme close-up (eyes, object, flame) and pull back, then back-and-up, to reveal the character, then the whole environment, ending in a wide or aerial view.
- WHIP (A-to-B FPV TRACK): start close to character A, accelerate fast through the environment (passing foreground pillars, trees, banners, soldiers, clouds), turn toward character B, decelerate smoothly into a close-up of B with a rack focus. Looks like an FPV drone flying through the real space.
- FPV (DRONE JOURNEY): a continuous flight starting near a character, moving away, accelerating through architecture or forest, turning toward another location, approaching another character, resolving into a new composition. Controlled speed ramps, banking, no teleporting.
- RISE (AERIAL REVEAL): begin near the ground (soldiers, grass, a character in the foreground), rise vertically and continue to a high or top-down view that reveals the formation, battlefield, forests and distant landscape.
- DIVE: start high above, descend smoothly toward a character or dramatic event, accelerating then decelerating before the subject, with strong parallax.
- ORB (ORBIT): smooth partial or full orbit (90-360 degrees) around a character or object, used for divine appearances, confrontations, transformations and revelations. Reveals the surrounding 360-degree world.
- LOWFPV: camera close to the ground weaving between trees, rocks, pillars, buildings and soldiers with strong foreground parallax.
- CRANE / SWEEP: crane up, crane down, lateral tracking, overhead sweep, gentle banking, high and low angles for scale.
- TRACK / FOLLOW: follow a walking, running or riding character from behind, beside or ahead.
- THRU (FLY-THROUGH): pass through a doorway, an arch, a gap in trees, a cloud bank, a flame or a character's eye to arrive in the next composition (natural scene change).
- ARROWCAM: ride along with a flying arrow, chakra or astra through the world until impact.
- RACK: shift focus between near and far subjects.
- DOLLYZ: rare dolly-zoom for a shocking realisation.
- LOOP: a compound sequence that chains several of the above (11.6).

### 11.6 SIGNATURE CHOREOGRAPHIES (templates; adapt the details to the scene)
1. THE LOOP (character, environment, object, aerial): ECU-F on character A's eyes (hold about 1 s) -> WHIP to character B passing a foreground pillar/tree, banking slightly, ending in B's close-up with rack focus (about 1.2 s) -> PB: pull back and rise in an arc, revealing both characters and the full environment (about 3 s) -> glide to an important object on the ground or in a hand (about 1.5 s) -> ECU-O (hold about 0.8 s) -> RISE to a top-down drone view of the whole location (about 3.5 s) -> optionally DIVE into the next event. Total roughly 14-20 s.
2. DIVINE ARRIVAL: low-angle start looking up, ORB around the deity (90-180 degrees) as a golden light burst, halo and particles bloom; end on a heroic wide with the environment reacting (trees bending, birds scattering).
3. BATTLE RISE: LOWFPV through soldiers' legs, banners and smoke -> RISE up through dust to a top-down view of the formations -> DIVE onto the hero/leader.
4. STORM ARRIVAL: calm wide -> RISE into the darkening, rolling clouds -> lightning flash -> DIVE through rain to the character, hair and cloth whipping.
5. ARROW SHOT: ECU-F eyes -> ECU-O bow and string -> release (heavy motion blur) -> ARROWCAM along the flight -> impact and aerial pull-back.
6. HOMECOMING / REVISIT: FPV flight toward a place the film has shown before, along a path consistent with its layout, so viewers recognise it immediately.
7. MEMORY / REFLECTION: slow CRANE up, soft light, low contrast, gentle drift.
8. REVEAL OF SCALE: LA on a giant with a tiny army below, slow rise to show the full scale.

### 11.7 CAMERA ENERGY PLAN AND CREATIVE DISCRETION
- Rate every beat with an ENERGY level: 1 (still-looking but drifting), 2 (gentle push/pull/track), 3 (flowing glide, crane, partial orbit), 4 (dynamic FPV, whip, dive, rise, full orbit), 5 (set-piece: chained LOOP).
- The camera is NOT constantly fast. Plan the film like music: calm passages, build-ups, bursts. As a guide, about 30-40 % of the runtime sits at energy 4-5, grouped into set-pieces of roughly 6-20 s; about 30 % at energy 3; the rest at 1-2. Never run energy 4-5 for more than about 15 s without a calmer breathing beat.
- Spend high energy where the story earns it: introductions, reveals, arrivals, confrontations, transformations, journeys, battles, climaxes, scene changes. Spend calm energy on peaceful, emotional, reflective and informational narration.
- Wherever your cinematic judgement says a loop, orbit, ECU, drone view, dive or aerial reveal would make the film feel more like a real movie, add it, as long as it suits the narration. Over a long film, aim to have used every move in the dictionary at least once if the story supports it, and never repeat the same move twice in a row.
- Every storyboard row must contain a short WHY (story reason) for its move.
- Vary shot sizes: no more than 2 consecutive shots of the same size; alternate close, medium, wide and aerial.

### 11.8 LENS, DEPTH AND FOCUS
- FOV guide: wide/aerial/FPV 65-85 degrees (strong perspective and speed); standard 40-55 degrees; close-up and ECU 20-32 degrees (compressed, intimate, shallow depth of field).
- Depth of field: the focus plane follows the subject; background and foreground blur by distance; rack focus on hand-offs; foreground bokeh (leaves, grass, insects, raindrops, embers) passes the lens for depth.
- Stage every shot in depth: foreground element, subject plane, midground, background; avoid flat compositions.
- Composition: rule of thirds, look-room, leading lines (paths, rivers, pillars, rays), the subject lit by a clear light source.

### 11.9 TRANSITIONS (cinematic, camera-driven first)
- Preferred: continuous camera travel through the world (THRU, FPV, RISE, DIVE, whip) so scenes flow into each other without cuts.
- WHIP CUT: a fast whip with heavy motion blur whose blur covers the swap to the next location; match the direction and velocity at both ends.
- PASS-THROUGH WIPE: a foreground object (tree trunk, pillar, cloud, banner, flame, hand) crosses the lens and covers the frame, then clears to the next scene.
- MATCH CUT / MATCH DISSOLVE: keep a shape, character or motion in the same place while the world changes around it.
- LIGHT DIP: the scene brightens into a warm glow, then the next scene fades up from it.
- CROSS-DISSOLVE (0.6-1.0 s) for calm, reflective passages; FADE THROUGH BLACK only at the start, the end, or large time jumps.
- Never: spins, page turns, shape wipes, glitch effects, cartoon swooshes, flashy gimmicks. Transitions between different locations must not teleport: some continuity cue (motion direction, light, a shared element) always links them.

### 11.10 THE WORLD KEEPS MOVING DURING CAMERA MOVES
The living world runs on the global clock and is independent of the camera. While the camera whips, orbits or dives, the trees keep swaying, clouds keep drifting, water keeps flowing, rain keeps falling, fires keep flickering, birds and butterflies keep flying, hair and cloth keep moving, particles keep floating and characters keep breathing and acting. Nothing freezes or restarts when the camera arrives, and the motion blur is applied on top of live motion.

---------------------------------------------------------------------

## 12. STORYTELLING, PACING AND SHOT GRAMMAR

- A new composition or camera idea about every 3-6 s; peaceful or emotional narration may hold 8-12 s with gentle motion. Do not turn the film into a frantic montage and do not leave anything static.
- One idea per shot. If the narration lists items (for example four reasons), show them as consecutive shots.
- Film structure for each narrative unit: ESTABLISH (wide or aerial) -> INTRODUCE (close/medium, reveal) -> DEVELOP (coverage, reaction, details, ECU of objects) -> PAYOFF (the dramatic move or image) -> BREATHE (calm). Open the film on a strong image (no logo or intro card) and end on a calm, wide, still-breathing image that fades to black.
- Emotion to camera mapping: calm = wide + gentle drift; devotion = slow push to close-up; revelation = pull-back; threat = low angle + slow push; divine = orbit + low angle + glow; grief = slow push, desaturated, rain/mist; journey = FPV or aerial glide; battle = aerial rise, low FPV, impacts; victory = crane up with warm light; ending = slow crane up and fade.
- FLASHBACK / MEMORY: washed-out, low-contrast, warm cream-tinted version cross-dissolving with the present.
- SCRIPTURE/QUOTE narration: show a library or temple scene with scrolls and lamps, with unreadable decorative glyphs only (never readable text).
- SYMBOL shots for abstract ideas (a lamp, lotus, sundial, chakra) lit against a dark rich background with floating particles.
- Time passing: clouds racing, sun and moon moving, seasons changing, lamps burning down.
- Keep the lower 15-20 % of the frame calm where possible (the ground line around 78-85 % of the frame height in static compositions) and the subject placed on thirds.
- KEYWORD TO VISUAL MAPPING (fast storyboard; originally for Ramayana, extend by analogy to any story). Anything not covered: choose the closest environment and shot type and build it in the same style:

- Ravan, Lanka, demon king, ten heads -> Ravan hero shot / Lanka night.
- Brahma, boon, blessing, creator -> Brahma on lotus in golden clouds.
- Vishnu, avatar, chakra, divine -> Vishnu four-armed in blue-grey clouds with halo.
- Ram, Lakshman, bow, arrow -> Ram/Lakshman in forest ashram or open plain; arrow streaks.
- Parshuram, axe, Brahmin warrior -> Parshuram hero shot on cloud hilltop (back view) or forest ashram.
- Sita, abduction, captivity -> Ashoka grove at night / chariot in sky.
- Text, verse, sarga, kand, Purana, scripture -> scripture library with scrolls.
- War, battle, army, killed -> battle plain, armies silhouettes, arrows, red sky, smoke (no gore).
- Time, later, years, then -> sundial/clock symbol or sky time-lapse (clouds moving fast and fading).
- Giant, Kumbhakarna -> low-angle giant over army in front of Lanka sunset.
- Sage, hermit, donate, penance -> rishi meditating at the forest ashram campfire.
- Death, tragedy, cruelty, darkness -> dark mural gallery, candle glow, slow pan.
- Hope, compassion, conclusion -> warm golden light, Ram figure glowing in a niche or hilltop silhouette at dusk, then fade to black.

---------------------------------------------------------------------

## 13. BACKGROUND MUSIC (mandatory; calm and gentle by default, changing with the scene)

- Music is always present: instrumental only, no vocals, no lyrics. Original (composed/synthesised in code) or properly licensed. If you synthesise it, make it genuinely musical (real melodic phrases, harmony, slow evolving textures, reverb) and say honestly in the summary that it is synthesised.
- DEFAULT MOOD: calm, gentle, emotional, reverent. Loud or dramatic passages appear only when the story truly demands (battle, climax), and even then stay controlled and never harsh.
- Instrument palette: soft Indian bansuri flute, soft orchestral strings, warm ambient pads, subtle piano, tanpura drone and texture, delicate temple bells, celestial chimes, low cinematic drones, restrained orchestral percussion (frame drums, soft timpani, taiko-like hits only for battle), light sitar or santoor touches sparingly.
- MUSIC MAP: before building, plan at least 4-6 distinct musical sections that follow the story's emotional arc (for example: calm opening, building curiosity, tension/conflict, climax/battle, resolution/victory or sorrow, peaceful close). NEVER loop one track for the whole film. Change sections on narration pauses or phrase boundaries with 2-4 s crossfades (or a tanpura/pad bridge). The music changes with the scene's mood, location and time of day.
- Level: generally 18-25 dB below the narration, adjusted per scene, ducked automatically while the voice speaks. Short swells (up to about 2 s, never above about 12-14 dB under the voice) only in narration pauses, then duck back. Music must never cover a word.
SCENE TO MUSIC
- PEACEFUL FOREST / ASHRAM / DAWN: soft bansuri over a tanpura drone, gentle pads, subtle birdsong ambience, slow tempo (about 50-65 bpm or free time).
- DIVINE APPEARANCE: celestial pads, delicate temple bells and chimes, soft strings in warm sacred harmony, gentle swell with the light burst.
- EMOTIONAL / SORROW: sparse piano, emotional strings, soft low pad, slow tempo, space between notes.
- SUSPENSE / NIGHT: low drones, restrained tension, quiet textures, a distant bell, no melody or only a sparse one.
- JOURNEY / TIME PASSING: flowing strings and pads with light pulsing rhythm.
- STORM: low drone with rising texture, distant timpani swell, no cheerful elements.
- BATTLE: powerful cinematic orchestral layers, controlled percussion, brass-like synth swells, dramatic but clean impacts.
- VICTORY / DEVOTION: uplifting strings and flute with warm harmonies and divine ambience.
- CLOSING: peaceful flute, gentle strings and pads, a complete emotional resolution that ends cleanly.
PITCH MATERIAL (use as modes/scales so the music sounds Indian-cinematic): Bhoopali (pentatonic S R G P D) for peace and dawn; Yaman (with raised 4th) for evening devotion; Bhairav (flat 2nd and 6th) for solemn morning/sacred seriousness; Bhairavi (flat 2nd, 3rd, 6th, 7th) for sorrow; Marwa-like (flat 2nd, raised 4th, no 5th) for unease. Keep a steady tanpura drone on the tonic and fifth under sacred and calm passages.
SYNTHESIS RECIPES (when no licensed library is available): bansuri = breathy sine/triangle with band-limited noise, slow vibrato (5-6 Hz), gentle attack and portamento; tanpura = four plucked strings (Karplus-Strong) cycling about every 4-6 s with long decay; strings = detuned sawtooth ensemble through a low-pass filter with slow attack and release; pads = filtered detuned oscillators with slow modulation; piano = additive or FM with a natural decay; bells and chimes = inharmonic partials with long exponential decay; reverb = convolution or a Schroeder/feedback-delay network sized per environment; stereo width through slight detune and chorus.

## 14. SOUND EFFECTS (mandatory, scene-specific, timed to the picture)

- Build an SFX CUE SHEET (audio_cues.json): time, sound, layer, level, pan, reverb send. Place every sound on the frame of the visual event it belongs to. Nothing random.
- ENVIRONMENT BEDS (continuous, low): forest ambience, wind through trees (level follows the wind value), birds, flowing water, leaves moving, crickets and owls at night, rain (follows rain intensity), thunder (arrives after the lightning flash), fire crackle (follows flame size), sea, crowd murmurs, distant army, temple bells.
- CHARACTERS: footsteps (matched to the surface: soil, grass, stone, wood, water, sand) landing exactly on foot plants, cloth movement, jewellery jingle, breathing at big efforts, weapon handling, bowstring tension and creak, bowstring twang at release, arrow whoosh with a Doppler-like pitch shift, arrow impact thud, sword swing and clash, mace, armour movement, chariot wheels and horse hooves.
- CAMERA: subtle air movement and soft whooshes scaled to camera speed (only on fast FPV, whip and dive moves); never cartoon swooshes.
- DIVINE: gentle bells, celestial chimes, soft magical energy textures, soft divine impacts, warm choral-like pad swells (no words).
- BATTLE: distant army ambience, weapon clashes, arrow volleys, impacts, fire and explosion rumble (no gore sounds).
- WILDLIFE: bird calls, butterfly-wing and insect buzz at very low level, bats, owl hoots, frogs.
- SYNTHESIS RECIPES (if no library): wind = band-passed noise with an LFO driven by the wind value; rain = layered filtered noise with random drop ticks; thunder = low-passed noise burst plus a long low rumble with reverb; fire = random short clicks over filtered noise; footsteps = short filtered noise thump plus a high-frequency scuff per surface; cloth = short band-passed noise swish; bowstring twang = fast-decaying damped sine/Karplus-Strong at about 180-400 Hz; arrow whoosh = band-passed noise sweep with a pitch glide; metal clash = inharmonic partials with a short noise burst; bells = inharmonic partials; birds = FM sweep chirps with a natural rhythm; water = filtered noise with random bubbles; insects = narrow-band modulated noise at 200-300 Hz.
- SPATIAL: pan by the object's screen position, attenuate and low-pass with distance, add environment reverb (damp and short in a forest, long in a palace hall or cave, almost none in open fields).
- Vary repeated sounds (several variants, slight pitch and timing changes) so nothing sounds mechanical. Levels: ambience beds about 28-35 dB under the voice, ordinary SFX about 24-32 dB under, big impacts at most about 18 dB under. Nothing harsh, artificial or fatiguing.

## 15. PROFESSIONAL AUDIO MIX

- THREE SYNCHRONISED LAYERS: (1) ORIGINAL VOICEOVER, (2) scene-specific music, (3) scene-specific SFX and ambience.
- Process internally in 32-bit float at 48 kHz. Resample the voiceover to 48 kHz only if its source rate differs, using a high-quality resampler (this does not change speed or pitch).
- The voiceover stays at its original level and dynamics (gain 0 dB). No EQ, noise reduction, compression, normalisation or effects on it.
- DUCKING: drive the music (and, lightly, the SFX beds) from the voiceover's envelope (for example ffmpeg sidechaincompress with threshold about 0.03-0.05, ratio 6-10, attack 20-50 ms, release 400-700 ms, or a numpy envelope follower), on top of the static 18-25 dB offset, so the voice is always clearly in front. Check word by word that no narration is masked.
- Smooth fades and crossfades; no abrupt audio changes. Music may begin before the first word (about 1-2 s) and must resolve after the last word with a calm tail of at most about 3 s, finishing with a gentle fade; the picture fades to black over the last 1-1.5 s.
- MASTER: only a master gain and a true-peak limiter at about -1 dBTP to prevent clipping; consistent loudness; no distortion. Verify peak and clipping numerically.
- Encode the final audio into the MP4 as AAC 48 kHz, 256 kbps or higher. Deliver the untouched voiceover separately as ORIGINAL_VOICEOVER.m4a.

## 16. ABSOLUTELY NO ON-SCREEN TEXT

The final video contains NO subtitles, captions, titles, chapter cards, lower thirds, quotes, scripture overlays, logos, watermarks, channel names, promo screens, UI elements, emojis or any other text. Props and clothing never show readable writing (decorative glyph patterns only). The story is told through illustration, animation, camera, light, atmosphere and sound. Run a check on sample frames before delivery.

## 17. DELIVERABLES

Always produce all three as real downloadable files and present the real links:
1. COMPLETE_FINAL_VIDEO.mp4: the primary deliverable. 2560x1440, 60 fps, H.264, yuv420p, AAC 48 kHz, with the original voiceover, music, SFX and final colour grade in sync.
2. ORIGINAL_VOICEOVER.m4a: the unaltered source narration.
3. SOURCE_PROJECT.zip: engine code, data files (cast, locations, storyboard, weather timeline, camera keyframes, audio cues), generated assets, render and mix scripts, production notes.
In the final chat message give: the cast sheet (compact), the location list, the storyboard (compact), "camera validation: 0 violations", the verified specs from ffprobe (codec, resolution, fps, pixel format, audio rate, duration), and one or two lines about any limitation. Keep it short.

## 18. FINAL QUALITY CHECKLIST (fix every "no" before delivering)

FIRST: all five gates from Section 0 (A animation proof, B framing proof, C audio proof, D export proof, E text-free proof) are PASSED and shown in the GATE REPORT.

VISUAL
1. Every narration beat has a matching scene; the timeline equals the voiceover duration (plus the short tail); nothing omitted or reordered.
2. Characters match their cards in every scene and are detailed and script-accurate (face, costume, ornaments, props); hair, cloth and jewellery move with physics.
3. EVERYTHING MOVES: Gate A passed. Characters, hair, cloth, jewellery, trees, grass, clouds, water, fire, smoke, creatures, rain and light all visibly animate in every scene, with the camera locked as well as moving. A moving camera over still pictures is a failure.
4. The living world is present and fits the story timeline: correct time of day, weather, wind, plants, animals, insects, water, fire, fireflies at night.
5. Revisited places are identical to their first appearance (locations.json registry); new places are unique.
6. Palette, lighting, bloom, depth fog, depth of field, vignette, grain and grade present on every shot; violence is implied, never graphic.
7. No on-screen text anywhere.
CAMERA
8. Gate B passed (framing_log shows 0 violations, runtime clamp active): no subject leaves the safe frame (except flagged hand-offs and deliberate ECUs), no half-cut characters, no empty edges, pitch/roll limits respected.
9. Moves are smooth: C2-continuous paths, eased speed ramps, banking, motion blur only on fast moves, strong parallax, no teleporting, no jerk, no stutter.
10. Shot sizes and moves are varied; high-energy set-pieces are motivated by the story; calm beats stay calm but alive; background keeps animating through every move.
AUDIO
11. The original voiceover is preserved exactly (content, order, speed, pitch, dynamics) and clearly audible; ORIGINAL_VOICEOVER.m4a delivered.
12. Music is present in several scene-appropriate sections, calm and gentle by default, ducked under the voice, never covering a word.
13. SFX are synchronised to visual events (thunder after lightning, footsteps on foot plants, bow release, arrow flight), balanced, not repetitive, not harsh; no clipping; the ending is clean.
EXPORT (verify with ffprobe, do not guess)
14. The file really is MP4: H.264, yuv420p, 2560x1440, 60 fps, AAC 48 kHz, faststart, and plays on Android. Not a renamed WebM.
15. Video duration matches the audio; A/V sync checked at the start, middle and end.
16. The download links point to the real finished files.

## 19. STRICT DO / DON'T

DO
- Follow the reference videos and script for the exact look; add detail, depth, motion and cinematography on top.
- Keep every scene alive with gentle, smooth, calm motion; keep the camera moving purposefully where the scene demands it.
- Keep characters and locations consistent; reuse a place exactly when the story returns to it.
- Use fast, dramatic, smooth 3D-feeling camera work (close-ups, whips, orbits, drone and aerial views, loops) where the story earns it, and always keep the subject framed.
- Add real-world life (weather, wind, time of day, wildlife, fireflies, water, fire) wherever it fits.
DON'T
- NO on-screen text of any kind.
- NO video where only the camera moves while characters and environments stay still pictures.
- NO realistic 3D models, NO anime/chibi/comic style, NO children's-cartoon look, NO flat static slideshow.
- NO gore, blood or dismemberment.
- NO camera that leaves characters out of frame or cuts them in half (except a deliberate extreme close-up), NO sudden teleporting between locations, NO constant shaky camera, NO random zooms, NO excessive spinning.
- NO replacing, regenerating, speeding up, slowing down or processing the voiceover.
- NO WebM/HTML substitutes for the MP4, NO fake 60 fps by frame duplication, NO upscaled low resolution called native 2K.
- NO stopping at a plan, preview or code; NO claiming success without a verified file.

## 20. KNOWN PROBLEMS FROM THE PREVIOUS VIDEOS AND THEIR FIXES

- ONLY THE CAMERA MOVED; characters, environments and everything else were still pictures -> the six animation layers and Gate A (Section 0), the animation engine (Section 22), the motion mandate with measurable minimums (Section 23). A moving camera over still images is a failed video.
- CHARACTERS LEFT THE FRAME OR WERE CUT OFF -> framing rules (11.2) enforced by the runtime clamp fit_camera() on every frame, logged and checked by Gate B (Section 24).
- Camera too slow and not smooth -> energy plan with real fast moves where needed (11.7), C2-continuous splines, speed ramps and motion blur (11.3), sub-pixel rendering and true 60 fps (3.2).
- Characters not detailed and hair frozen -> character cards and face/ornament systems (6), part-based puppet rigs and physics-driven hair, cloth and jewellery (7.3, 22.4).
- Repetitive visuals -> shot variety, energy planning and unique environments (8, 11.7, 12).
- Weak or missing music and sound effects -> mandatory scene-specific music and SFX with a cue sheet and mix (13-15).
- Output not a proper MP4 -> strict 2560x1440, 60 fps MP4 pipeline with verification (0, 3.6, Gate D).

## 21. HOW TO START WHEN THE USER SAYS "MAKE THE VIDEO"

1. In one short message: confirm the four inputs received (or name what is missing), the voiceover duration, that you will deliver a 2560x1440, 60 fps MP4, and that you will PROVE animation (Gate A) and framing (Gate B) before the full render.
2. Immediately do the work in the order of Section 2: analyse references, script and voiceover; show the compact cast sheet, location list and storyboard (with ACTION VERBS, energy level and WHY per shot).
3. Build the engine following Sections 22-24. Run Gate A and Gate B and show the GATE REPORT table (rows: A character motion score, A environment motion score, A sky motion score, A stillness grid, A amplitude check; B frames checked, B violations, B corrections applied). Fix and re-run until they pass.
4. Render in chunks, mix, encode, then run Gates C, D and E. Deliver the three files with a short final summary and the verified specs.
5. Do not ask for permission to continue between steps. Ask a question only if something truly blocks the work.

---------------------------------------------------------------------

## 22. THE ANIMATION ENGINE: HOW TO MAKE EVERYTHING MOVE IN CODE

### 22.1 Core principle and frame order
- A moving camera over still pictures is NOT animation. Every character, plant, cloud, water surface, flame, creature and particle must be re-drawn or re-warped on EVERY frame as a function of time t. No element that should move may show the same pixels on two consecutive frames.
- Strict order for every frame n: (1) t = n / 60; (2) update the world simulation (wind, weather, water, fire, creatures, particles); (3) pose every character (script action clip + idle layer + secondary physics); (4) animate the environment layers (warps and loops); (5) update lights and shadows; (6) collect every drawable with its world position; (7) evaluate the camera path and run the runtime framing clamp (Section 24); (8) project and composite back to front; (9) post-process (depth of field, motion blur, bloom, grade, vignette, grain); (10) write the frame. The world is animated BEFORE the camera sees it, so the camera always travels through a moving world.
- Never freeze an element to save time. If compute-limited, lower the resolution of the displacement fields, reduce particle counts, or use lower sprite detail for distant objects. Never swap animation for a still image.

### 22.2 Asset routes (mix freely, but every route must produce real per-frame motion)
- ROUTE A: code-drawn layered vector puppets and props. Best sharpness for close-ups. Draw each part from paths with its own transform every frame.
- ROUTE B: generated illustrations separated into layers.
  - Characters: generate each character (and each costume state) on a plain flat keyed background, ideally as an "exploded part sheet": head (front and three-quarter views), hair back and front, torso, upper arm and forearm+hand for left and right, legs, cloth pieces (pallu, cape, dhoti end), ornaments, weapon/prop. Alternatively generate the whole figure and cut parts with polygon masks defined from the cast card and the joint positions. Key out the background to RGBA.
  - Environments: generate as separate depth layers (sky, far, mid, near, foreground framing elements) with transparent cut-outs; trees, foliage, grass, flags, water, fire and smoke as separate elements so each can be animated independently; extend layers beyond the frame (overscan) so camera moves never reveal edges.
  - Keep ONE consistent style prompt, include the cast card text in every generation, and reuse the same part images for the same character in every scene.
- A character that is a single flat image with only camera motion applied FAILS Gate A. A background that is one flat picture FAILS Gate A.

### 22.3 Universal warp animation (guaranteed visible motion on any image layer)
For any RGBA layer, compute a displacement field D(x, y, t) at low resolution (1/8 to 1/16 of the layer), upsample it bilinearly, and apply it with cv2.remap. Soft motion masks keep the roots fixed and let the tips move most: weight w(y) = ((anchor_y - y) / anchor_y)^1.5 (0 at the root, 1 at the tip), so trunks, stems and the top of a hanging cloth stay anchored while canopies, tips and hems move.
- Wind sway: dx = A * w * (0.7 * waveA + gust), with waveA = sin(2*pi*(f*t + kx*x + ky*y) + phase) + 0.5*sin(2*pi*(3.1*f*t + 2*kx*x) + 1.7*phase); a smaller dy for natural curl. Use the global wind value (Section 9.3) for gust and strength.
- Apply it to: tree canopies and leaf clusters, grass, flowers, bamboo, hair, beards, saree pallu, capes, hems, garlands, banners (use a travelling wave along the length), hanging roots, tents, smoke plumes, flames (with vertical flicker), water surfaces (ripples), cloud edges (slow morph) and reflections.
- Use different phases and frequencies per element so nothing moves in lockstep. Amplitudes must meet the minimums in Section 23.1.

### 22.4 Character puppet rig (part-based cut-out with real joints)
- HIERARCHY: pelvis (root) -> torso -> neck -> head; torso -> upper arm (L/R) -> forearm -> hand; pelvis -> thigh (L/R) -> shin -> foot. Separate layers: hair back, hair front, cloth/pallu, garlands, jewellery pieces, crown/feather, weapon/prop. Each part has a pivot at its joint. Child positions come from forward kinematics: child_pos = parent_pos + R(parent_angle) * child_offset.
- DRAW ORDER (back to front): back hair, back arm, back leg, torso and clothes, front leg, head, face features, front hair, crown, front arm and prop, foreground cloth. Swap draw order when the character turns (turntable view sets, Section 7.1).
- IDLE LAYER (always on, every character, random phase): breathing (torso scale 1.5-2.5 % about the waist, shoulders rise 5-8 px, period 3-4 s), weight shift (hips move 6-15 px every 4-8 s), head micro-rotation (+/-1.5 to 3 degrees, slow), blink every 3-6 s (an eyelid layer scales over the eye for 0.12-0.18 s), gaze shifts (the pupil/iris layer offsets 2-6 px toward the look target, eyes lead the head by 0.1-0.2 s), small hand and finger movement every 2-4 s.
- ACTION CLIPS: build keyframe tables (time, joint angles, positions) with cubic ease for every action in Section 7: walk, run, sit, kneel, bow, namaskar, abhaya mudra, point, beckon, embrace, lift, carry, cry, anger, think, ride, fly/levitate, sword/mace/axe swing, chakra throw, and the nine archery phases (7.7). Blend the clip on top of the idle layer. Narration decides which clip plays (22.9).
- SECONDARY PHYSICS: hair locks, beard, pallu, cape, garlands, feather, earrings and necklaces as chains (verlet or spring-damper) with the root attached to the moving part, pushed by the global wind and by the character's acceleration; render each chain as a warped strip or a rotated chain of small segments. Hair is NEVER frozen.
- FACE RIG: eyes (iris, pupil, highlight), eyelids, brows (rotate and offset), mouth shape (subtle smile or tension), cheeks; the expression set in 6.2 is built from these; blend over 0.3-0.6 s.
- If you only have a flat full-body image, you must still cut it into parts (polygon masks with soft edges) and rig it; a whole-figure warp alone is the minimum fallback for background extras only, never for hero characters.

### 22.5 Creatures and insects
Birds: 4-8 pose frames or a two-wing-part flap (wing rotation about the shoulder, 3-5 Hz) with glide phases, banking and flocks (V formations, circling kites). Butterflies: two wing parts whose width oscillates (scale x between 0.2 and 1.0 at 8-12 Hz) along a noise-driven wandering path with brief landings on flowers. Bees, flies, dragonflies: tiny sprites with a blur and looping/darting paths. Fireflies: additive glowing points with their own blink cycles and drift (9.5). Fish, frogs, deer, cows, monkeys, horses, elephants, serpents: idle cycles (tail, ears, head, breathing) plus gait cycles when moving. Always show some life in every outdoor shot (Section 23).

### 22.6 Water, fire, smoke, clouds, weather, light (procedural recipes)
- WATER: animated ripple displacement of the water layer and of the mirrored reflection, travelling sparkle noise, flow lines moving at the flow speed, foam at stones, splashes and rings when things touch it.
- FIRE: stack 3-5 flame sprites with noise-driven scale (0.9-1.1), lateral sway and colour ramp (white-yellow core to orange to red), additive blending; sparks and embers as rising particles with wobble; smoke particles that expand and fade; heat shimmer displacement above big fires; flicker the light it casts.
- CLOUDS: 3-5 layers drifting at different speeds with a slow edge morph (warp) and lit rims; storm clouds roll and darken.
- RAIN/SNOW/DUST: vectorised particle layers (far, mid, near, foreground bokeh) slanted by the wind; splashes, ripples and wet sheen on the ground.
- LIGHTNING: whole-scene flash (0.08-0.25 s, sometimes double) plus occasional polyline bolt and afterglow.
- GOD-RAYS and DUST MOTES: additive shafts whose opacity pulses 15-30 % over 6-8 s with slow sideways drift; motes drifting with the wind.
- LIGHT ON CHARACTERS: flame light flickers on nearby faces and cloth (colour 1800-2200 K, noise-driven intensity); dappled leaf shadows move across the ground and bodies; cloud shadows move over the land; ornaments glint when the light angle passes.

### 22.7 Performance and feasibility (without cutting animation)
- Compute displacement fields at low resolution and upsample; cache loops of noise fields; pre-render static far layers; render only dirty regions where possible; process in float32/uint8; composite with regions of interest, not the whole 2560x1440 canvas, for small sprites.
- Parallelise by chunk (Section 3.5). Benchmark a 3-second full-resolution clip first, then plan chunk sizes. Keep the animation; cut cost elsewhere (fewer particles, lower-resolution fields, smaller regions).
- Pre-rasterise parts at 1x, 2x and 4x for sharp close-ups (3.2). Draw extreme close-ups from the highest detail level.

### 22.8 Order of work (so animation is never forgotten)
Build and test in this order: (1) one character with idle layer + two action clips on a flat background, camera locked, confirm motion; (2) one environment with wind, clouds, water or fire, creatures and particles, camera locked, confirm motion; (3) combine; (4) add the camera and the runtime clamp; (5) scale to all scenes. Only then render the film.

### 22.9 Script-to-action mapping (drives what every character does)
For every beat, list the verbs and states in the narration and map them to clips. Every visible character performs at least one narrative action per beat on top of the idle layer, unless the story says they are still (for example meditating: still body but breathing, drifting hair and cloth, glowing aura, falling petals).
- walked, travelled, went, returned -> walk or run cycle (with camera follow), dust, cloth drag.
- sat, meditated, prayed, waited -> seated breathing, subtle sway, slow blinks, hands in mudra.
- bowed, saluted, greeted -> namaskar and head bow with a body dip.
- said, told, asked, spoke, ordered -> gestures: a hand lifts or points, head nods or tilts, eyes move to the listener, shoulders shift.
- looked, saw, noticed -> head turn plus gaze shift, eyes widen if surprised.
- wept, grieved -> shoulders shaking, hands to face, tears, slow head lowering.
- smiled, blessed -> expression change, abhaya mudra, soft glow.
- angry, shouted, fought -> clenched fists, rigid stance, forward step, weapon raise.
- shot an arrow, drew a bow -> the nine archery phases (7.7) with arrow flight and impact.
- swung, struck, attacked -> sword/mace/axe clip with trail and impact.
- rode, drove a chariot -> riding clips, wheels turning, horses galloping, dust trail.
- flew, rose, descended -> levitation or flight with trailing cloth and aura.
- appeared, vanished, transformed -> light burst, particles, scale build-up.
- fell, died, slept -> controlled fall or lying pose with breathing; no gore.
- storm, rain, fire, flood, darkness -> weather and light layers escalate (Section 9).

### 22.10 Reference code (illustrative; adapt, test and keep correct)
```python
import numpy as np, cv2

def wind_warp(layer_rgba, mask, t, anchor_y, A=18.0, f=0.35, kx=0.004, ky=0.002,
              phase=0.0, gust=0.0, small=8):
    """Warp an RGBA layer with a wind-sway displacement field.
    mask: float32 0..1 (where motion is allowed) or None. anchor_y: row of the fixed root
    (use the bottom row for trees and grass; for hanging cloth flip the weight)."""
    h, w = layer_rgba.shape[:2]
    sh, sw = max(h // small, 2), max(w // small, 2)
    ys, xs = np.mgrid[0:sh, 0:sw].astype(np.float32)
    X, Y = xs * small, ys * small
    height_w = np.clip((anchor_y - Y) / max(anchor_y, 1.0), 0, 1) ** 1.5   # 0 root, 1 tip
    m = cv2.resize(mask.astype(np.float32), (sw, sh)) if mask is not None else 1.0
    wave = (np.sin(2*np.pi*(f*t + kx*X + ky*Y) + phase)
            + 0.5*np.sin(2*np.pi*(3.1*f*t + 2*kx*X) + 1.7*phase))
    dx = (A * (0.7*wave + gust) * height_w * m).astype(np.float32)
    dy = (0.25 * A * np.sin(2*np.pi*(1.3*f*t + ky*X)) * height_w * m).astype(np.float32)
    dxf = cv2.resize(dx, (w, h), interpolation=cv2.INTER_LINEAR)
    dyf = cv2.resize(dy, (w, h), interpolation=cv2.INTER_LINEAR)
    gx, gy = np.meshgrid(np.arange(w, dtype=np.float32), np.arange(h, dtype=np.float32))
    return cv2.remap(layer_rgba, gx + dxf, gy + dyf, cv2.INTER_LINEAR,
                     borderMode=cv2.BORDER_CONSTANT, borderValue=(0, 0, 0, 0))

def draw_part(canvas_bgra, part_bgra, pivot_xy, joint_pos_xy, angle_deg, scale=1.0):
    """Draw a puppet part rotated about its pivot so the pivot lands on joint_pos_xy.
    (In production, warp only the part's bounding region, not the whole canvas.)"""
    M = cv2.getRotationMatrix2D((float(pivot_xy[0]), float(pivot_xy[1])), -angle_deg, scale)
    M[:, 2] += np.array(joint_pos_xy, dtype=np.float64) - np.array(pivot_xy, dtype=np.float64)
    warped = cv2.warpAffine(part_bgra, M, (canvas_bgra.shape[1], canvas_bgra.shape[0]),
                            flags=cv2.INTER_LINEAR, borderMode=cv2.BORDER_CONSTANT,
                            borderValue=(0, 0, 0, 0))
    a = warped[..., 3:4].astype(np.float32) / 255.0
    canvas_bgra[..., :3] = (warped[..., :3] * a + canvas_bgra[..., :3] * (1 - a)).astype(canvas_bgra.dtype)
    canvas_bgra[..., 3:4] = np.maximum(canvas_bgra[..., 3:4], warped[..., 3:4])
    return canvas_bgra

def motion_score(gray_frames, mask=None, step=30):
    """gray_frames: list of float32 greyscale (0-255) frames at 60 fps rendered with the
    CAMERA LOCKED. Returns the mean absolute change over 0.5 s (step=30 frames)."""
    diffs = [np.abs(gray_frames[i + step] - gray_frames[i])
             for i in range(0, len(gray_frames) - step, 10)]
    d = np.mean(diffs, axis=0)
    return float(d[mask].mean()) if mask is not None else float(d.mean())
```

---------------------------------------------------------------------

## 23. THE MOTION MANDATE AND THE ANIMATION PROOF (GATE A)

### 23.1 Minimum visible motion (at 2560x1440; "calm" means a peaceful scene, bigger in wind or action)
- CHARACTER BREATHING: shoulders and chest rise 5-8 px (1.5-2.5 % of body height), period 3-4 s, always.
- WEIGHT SHIFT: hips and torso shift 6-15 px every 4-8 s. HEAD: slow rotation +/-1.5 to 3 degrees. BLINKS every 3-6 s. GAZE shifts every 2-5 s. HANDS: visible movement every 2-4 s.
- NARRATIVE ACTION: at least one action clip per beat for every visible character (22.9).
- HAIR and BEARD: tip movement 6-12 px in still air, 15-40 px in wind.
- CLOTH (pallu, cape, hem, dhoti end): 15-45 px with a travelling wave. BANNERS and FLAGS: 30-80 px.
- JEWELLERY, GARLANDS, FEATHERS: swing +/-3 to 8 degrees, 6-20 px, with occasional glints.
- TREES: canopy sway 10-30 px, leaf-cluster flutter 3-8 px at 1.5-3 Hz, at least one falling leaf or petal every 2 s in a forest shot.
- GRASS, CROPS, FLOWERS: 6-20 px travelling waves.
- CLOUDS: drift 20-60 px/s (far layers 10-25 px/s) with slow shape morph.
- WATER: ripples 3-6 px, flow 30-120 px/s, shimmering reflections.
- FIRE: lateral flicker 8-25 px, height flicker about 10 %, rising sparks; flame light flickers at 5-12 Hz on nearby surfaces.
- SMOKE and MIST: drift and rise 20-60 px/s with expansion.
- CREATURES: at least 2 living creatures visible in every outdoor wide shot (birds, butterflies, insects, animals); butterflies flap 8-12 Hz; birds 3-5 Hz.
- RAIN: three speed layers, near drops 1200-2600 px/s, slanted by wind, with splashes.
- LIGHT: god-ray opacity pulse 15-30 % over 6-8 s; dappled light moving 10-30 px/s; cloud shadows drifting.
- CAMERA: micro-drift 0.5-1.5 % even in held shots (this is the last layer, never a substitute).
Amplitudes are small and smooth so peaceful scenes feel calm and alive, but they must be clearly visible, never imperceptible.

### 23.2 Per-shot rules
- Every shot moves in at least 4 of the 5 non-camera layers (character body, secondary, environment, life/weather, light).
- Every shot with a character shows the idle layer and at least one narrative action.
- Every shot contains at least 8 independent motions in total.
- STILLNESS RULE: no region larger than about 15 % of the frame area may stay motionless for more than 2 seconds (except a planned fade or pure darkness). Check it with an 8 x 4 grid: every cell must change by more than a small epsilon at least once every 2 s (sky cells: clouds or birds; ground cells: grass, dust, shadows, water; character cells: breathing, hair, cloth).

### 23.3 GATE A procedure (run before any full render, and spot-check again on the final timeline)
1. For each distinct location, and for each hero character (close and medium), render a 3-second clip (180 frames) at full resolution with the CAMERA LOCKED (static).
2. Compute motion_score() separately for the character mask (the alpha of the character layers), the environment (everything except characters), and the sky region.
3. Starting thresholds (mean absolute change in 8-bit grey levels over 0.5 s): character mask >= 1.0, environment >= 1.0, sky >= 0.3. They exist to prove real motion; never lower them to pass. If a clip looks lively but scores low, the visual strip decides, but explain why.
4. Run the stillness grid (23.2) and the amplitude check: log the peak displacement in pixels of each animated element and confirm it meets Section 23.1.
5. Extract a 6-frame strip at 0.5 s steps for each clip and LOOK at it: hair, cloth, leaves, clouds, water, flames and creatures must visibly differ from frame to frame.
6. Report the results in the GATE REPORT table. If anything fails, increase amplitudes, fix the rig or the layer separation, add missing animated layers, and run Gate A again. Do not start the full render until Gate A passes.
7. After the full render, re-render three random 3-second windows with the camera locked and repeat steps 2-5 as a spot check.

---------------------------------------------------------------------

## 24. THE FRAMING PROOF (GATE B) AND THE RUNTIME CLAMP

### 24.1 What to project
For every must-show subject, build a conservative 3D bounding volume in its CURRENT pose: width of the body including outstretched arms and cloth, full height including the crown, hair top, raised weapon and feet, and a small depth. Take the 8 corners of that volume and project them with the current camera. Union the boxes of all subjects in the shot's subject set.

### 24.2 The clamp (run on EVERY frame, after the camera path is evaluated, before rendering)
```python
import numpy as np

def cam_basis(pos, target, roll_deg=0.0):
    up = np.array([0.0, 1.0, 0.0])
    f = target - pos; f = f / np.linalg.norm(f)
    r = np.cross(f, up); r = r / np.linalg.norm(r)
    u = np.cross(r, f)
    if roll_deg:
        a = np.radians(roll_deg)
        r, u = r*np.cos(a) + u*np.sin(a), u*np.cos(a) - r*np.sin(a)
    return r, u, f

def project(pts, pos, target, fov_v_deg, aspect, roll_deg=0.0):
    """pts (N,3) world points -> (N,2) screen coords (0..1, y down) and depths."""
    r, u, f = cam_basis(pos, target, roll_deg)
    d = pts - pos
    x, y, z = d @ r, d @ u, np.maximum(d @ f, 1e-3)
    t = np.tan(np.radians(fov_v_deg) / 2)
    return np.stack([0.5 + 0.5*(x/z)/(t*aspect), 0.5 - 0.5*(y/z)/t], 1), z

def union_box(corner_sets, pos, target, fov, aspect, roll=0.0):
    pts = np.concatenate(corner_sets, 0)
    s, z = project(pts, pos, target, fov, aspect, roll)
    return s[:, 0].min(), s[:, 1].min(), s[:, 0].max(), s[:, 1].max(), z.min()

def limit_pitch(pos, target, max_deg=30.0):
    """Keep the camera height within +/-max_deg of the target (not for AERIAL shots)."""
    v = pos - target
    max_h = np.hypot(v[0], v[2]) * np.tan(np.radians(max_deg))
    p = pos.copy(); p[1] = target[1] + np.clip(v[1], -max_h, max_h)
    return p

def fit_camera(pos, target, fov, aspect, corner_sets, safe=(0.05, 0.05, 0.95, 0.95),
               roll=0.0, max_iter=16, aerial=False):
    """Return (pos, target, iterations). iterations == -1 means it failed: the caller
    must reuse the last known good camera for this frame and log it."""
    pos, target = pos.copy(), target.copy()
    for i in range(max_iter):
        if not aerial:
            pos = limit_pitch(pos, target)
        x0, y0, x1, y1, zmin = union_box(corner_sets, pos, target, fov, aspect, roll)
        if x0 >= safe[0] and y0 >= safe[1] and x1 <= safe[2] and y1 <= safe[3] and zmin > 0.3:
            return pos, target, i
        centre = np.concatenate(corner_sets, 0).mean(0)
        target = target + 0.6 * (centre - target)             # re-centre on the subjects
        view = pos - target; dist = np.linalg.norm(view); view = view / dist
        need = max((x1-x0) / (safe[2]-safe[0]), (y1-y0) / (safe[3]-safe[1]), 1.0)
        pos = target + view * dist * max(need * 1.08, 1.05)    # dolly back along the view axis
    return pos, target, -1
```
- Apply a critically damped spring to the correction (the difference between the planned and the fitted camera) so the clamp never produces a visible jerk. The planning pre-pass (11.2m) should already keep the corrections near zero.
- The clamp overrides every camera keyframe. If a flagged hand-off or deliberate ECU shot is in progress, use that shot's own crop rule instead (for example, the face box must be fully inside the frame) rather than the full-body rule.
- If the clamp cannot find a solution, use the last known good camera pose for that frame, log it, and after the pass fix the camera path and re-run.

### 24.3 Special framing rules
- Rise, crane and dive: move the camera position in world space, keep the target on the subject, let the subject get smaller, never let it leave. Aerial shots keep the subject at least 3.5 % of the frame height and inside the central 60 %.
- Orbits: radius from d = h / (2 * q * tan(theta / 2)) so the whole silhouette stays inside the safe frame at every angle.
- Close-ups: an ECU of a face includes both eyes and the brow fully; a crop never cuts through an eye. ECU of an object keeps the whole object feature (for example the arrow tip and the string) inside the frame.
- Whips and hand-offs: at every frame at least one of the two subjects or the travel path is in view; arrive with the next subject framed on a thirds line with look-room.

### 24.4 GATE B procedure
1. Write framing_log.json with, for every one of the N frames: shot id, each subject's projected box and margins to the safe frame, whether the shot is a flagged ECU/hand-off/aerial, the correction applied (or -1 for a failure).
2. After the render (or from the exact same camera and pose code), assert: zero frames with a non-flagged subject outside the safe frame; zero frames with empty edges; no pitch outside the limits except in flagged AERIAL shots; no NaN; no jumps.
3. Build a contact sheet of at least one frame per second plus every frame where a correction was applied, and LOOK at it: nobody is cut off, nobody left the frame, headroom and footroom look right.
4. Report "frames checked, violations, corrections applied" in the GATE REPORT. If violations exist, fix the camera path or the character blocking and run Gate B again. Do not deliver until it shows zero.
