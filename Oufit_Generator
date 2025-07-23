import React, { useState } from 'react';

// Temporary fallback data (in production these would be actual JSON imports)
const clothingData = {
  "tops": [
    {"id": 1, "item": "cropped tee", "formality": 1},
    {"id": 2, "item": "racerback crop", "formality": 1},
    {"id": 3, "item": "tank top", "formality": 1},
    {"id": 4, "item": "hoodie crop", "formality": 1},
    {"id": 5, "item": "linen camisole", "formality": 2},
    {"id": 6, "item": "off-shoulder crop", "formality": 2},
    {"id": 7, "item": "bandeau top", "formality": 2},
    {"id": 8, "item": "tube top", "formality": 2},
    {"id": 9, "item": "wrap blouse", "formality": 3},
    {"id": 10, "item": "turtleneck sweater", "formality": 3},
    {"id": 11, "item": "corset top", "formality": 3},
    {"id": 12, "item": "mock-neck top", "formality": 3},
    {"id": 13, "item": "fitted blazer", "formality": 4},
    {"id": 14, "item": "button-up shirt", "formality": 4},
    {"id": 15, "item": "silk wrap blouse", "formality": 4},
    {"id": 16, "item": "plunging silk gown top", "formality": 5}
  ],
  "bottoms": [
    {"id": 1, "item": "denim shorts", "formality": 1},
    {"id": 2, "item": "joggers", "formality": 1},
    {"id": 3, "item": "cargo pants", "formality": 1},
    {"id": 4, "item": "bike shorts", "formality": 1},
    {"id": 5, "item": "flared jeans", "formality": 2},
    {"id": 6, "item": "mini skirt", "formality": 2},
    {"id": 7, "item": "bodycon skirt", "formality": 2},
    {"id": 8, "item": "high-waisted jeans", "formality": 2},
    {"id": 9, "item": "high-waisted skirt", "formality": 3},
    {"id": 10, "item": "linen trousers", "formality": 3},
    {"id": 11, "item": "pleated midi skirt", "formality": 3},
    {"id": 12, "item": "leather skirt", "formality": 3},
    {"id": 13, "item": "tailored trousers", "formality": 4},
    {"id": 14, "item": "pencil skirt", "formality": 4},
    {"id": 15, "item": "split-front pencil skirt", "formality": 4}
  ],
  "shoes": [
    {"id": 1, "item": "white sneakers", "formality": 1},
    {"id": 2, "item": "flip-flops", "formality": 1},
    {"id": 3, "item": "canvas slip-ons", "formality": 1},
    {"id": 4, "item": "barefoot", "formality": 0},
    {"id": 5, "item": "platform sandals", "formality": 2},
    {"id": 6, "item": "combat boots", "formality": 2},
    {"id": 7, "item": "ankle boots", "formality": 3},
    {"id": 8, "item": "ballet flats", "formality": 3},
    {"id": 9, "item": "wedge heels", "formality": 3},
    {"id": 10, "item": "strappy heels", "formality": 4},
    {"id": 11, "item": "kitten heels", "formality": 4},
    {"id": 12, "item": "oxford shoes", "formality": 4},
    {"id": 13, "item": "stiletto pumps", "formality": 5}
  ]
};

const nsfwClothingData = {
  "tops": [
    {"id": 1, "item": "sheer mesh crop top", "formality": 2},
    {"id": 2, "item": "barely-there bandeau", "formality": 2},
    {"id": 3, "item": "cutout bodysuit", "formality": 3},
    {"id": 4, "item": "plunging halter top", "formality": 3},
    {"id": 5, "item": "backless corset", "formality": 4},
    {"id": 6, "item": "sheer blouse with no bra", "formality": 4},
    {"id": 7, "item": "deep-V silk slip top", "formality": 5},
    {"id": 8, "item": "completely sheer evening top", "formality": 5}
  ],
  "bottoms": [
    {"id": 1, "item": "micro-mini skirt", "formality": 2},
    {"id": 2, "item": "see-through leggings", "formality": 2},
    {"id": 3, "item": "cutout bodycon skirt", "formality": 3},
    {"id": 4, "item": "thigh-high slit pencil skirt", "formality": 4},
    {"id": 5, "item": "barely-there evening shorts", "formality": 4},
    {"id": 6, "item": "completely backless dress", "formality": 5}
  ]
};

const colorsData = {
  "neutral": ["Off-White", "Cream", "Warm Beige", "Taupe", "Light Gray", "Charcoal Gray", "Black", "Navy", "Camel", "Chocolate Brown"],
  "warm": ["Mustard Yellow", "Burnt Orange", "Terracotta", "Rust", "Coral", "Peach", "Brick Red", "Burgundy", "Copper", "Blush Pink"],
  "cool": ["Dusty Blue", "Teal", "Forest Green", "Olive Green", "Sage", "Mint", "Indigo", "Lavender", "Slate Blue", "Steel Blue"],
  "vibrant": ["Electric Blue", "Ruby Red", "Emerald Green", "Hot Pink", "Bright Coral", "Vivid Orange", "Kelly Green", "Fuchsia", "Turquoise", "Magenta"]
};

const locationsData = {
  "1": ["Walking along the beach at sunrise", "Sunbathing on volcanic rock", "Stretching on a rooftop terrace at dawn", "Stepping out of a freshwater stream"],
  "2": ["Sipping coffee at a sidewalk café", "Browsing handmade crafts at a market", "Reading on a bench overlooking the coast", "Walking home from dinner at dusk"],
  "3": ["Exploring ancient ruins under golden noon", "Attending traditional dance performance", "Strolling through historic streets at sunset", "Tasting wine in family-run vineyard"],
  "4": ["Boarding private yacht at sunset", "Pausing on staircase at summer art gala", "Walking through luxury boutiques in full glam", "Arriving at rooftop bar during storm light"],
  "5": ["Leaving VIP lounge at 2 AM", "Exiting cab wearing next to nothing", "Crossing bridge at twilight in evening gown", "Standing alone on cliffside terrace with wine"]
};

const actionsData = {
  "gentle": ["pauses to photograph surfers catching first light", "flips through a guidebook, stirring honey slowly", "leans slightly on sun-warmed stone", "turns a page slowly, breeze lifting the hem", "stops to adjust her camera"],
  "sensual": ["stretches slowly, arms overhead, her top lifting just enough", "one strap slipping off her shoulder as she stretches", "sleeps curled slightly, bare feet tucked beneath her", "reaches behind to fasten it, bare feet on cool tile", "kicks one off mid-step, carrying both barefoot"],
  "confident": ["steps carefully, one hand on the railing, fabric clinging from humidity", "strides past designer boutiques, one bare shoulder catching light", "turns slightly to check her reflection, dress tightening across hips", "walks slowly, one hand holding fabric closed", "laughing into her phone"]
};

const detailsData = {
  "regular": [
    "hair loosely braided as the warm wind lifts fine strands",
    "sunlight catches the highlights in her hair", 
    "she has a soft, knowing smile",
    "fabric clinging from humidity, eyes forward",
    "oil glistening on her tan under tropical sun",
    "bare legs glowing under streetlamps",
    "candlelight dancing across exposed skin",
    "her expression is relaxed and content",
    "wind lifting the hem with each step"
  ],
  "nsfw": [
    "curves perfectly accentuated by the skin-tight fabric",
    "drawing admiring glances from everyone nearby",
    "confidence radiating with every deliberate step",
    "fabric so sheer it leaves little to imagination",
    "outfit pushing the absolute limits of public decency",
    "moving with the assurance of someone who knows their power",
    "each curve highlighted by the strategic cutouts",
    "material clinging like a second skin",
    "turning heads with every confident stride"
  ]
};

const nsfwActionsData = {
  "teasing": [
    "adjusts her barely-there top with a knowing smile",
    "lets the fabric slip deliberately off one shoulder",
    "bends forward, testing the limits of her outfit",
    "stretches languidly, her top riding up dangerously",
    "poses confidently, completely unbothered by the stares"
  ],
  "bold": [
    "walks with complete confidence despite wearing almost nothing",
    "revels in the attention her revealing outfit draws",
    "adjusts her micro-skirt with deliberate slowness",
    "leans against the wall, fabric clinging to every curve",
    "moves with feline grace, each step calculated for maximum impact"
  ],
  "intimate": [
    "alone and unobserved, lets her guard down completely",
    "enjoys the freedom of wearing so little",
    "moves without concern for modesty in private",
    "stretches uninhibitedly, fabric barely containing her",
    "basks in the liberating feeling of minimal clothing"
  ]
};

const formalityRulesData = {"1": [1, 2], "2": [1, 2, 3], "3": [2, 3, 4], "4": [3, 4, 5], "5": [4, 5]};

const aiEnginesData = {
  "text": {
    "chatgpt": { "name": "ChatGPT (OpenAI)", "icon": "💬", "description": "Structured, organized format" },
    "gemini": { "name": "Gemini (Google)", "icon": "✨", "description": "Creative, flowing descriptions" },
    "local": { "name": "Local LLMs", "icon": "🖥️", "description": "Simple, direct prompts" },
    "grok": { "name": "Grok (xAI)", "icon": "🤖", "description": "Conversational, witty style" }
  },
  "image": {
    "midjourney": { "name": "Midjourney", "icon": "🎨", "description": "Artistic, cinematic style" },
    "dalle": { "name": "DALL-E (OpenAI)", "icon": "🖼️", "description": "Natural language prompts" },
    "flux": { "name": "Flux", "icon": "📸", "description": "Photorealistic, technical details" },
    "hidream": { "name": "HiDream", "icon": "🌙", "description": "Artistic, dream-like quality" },
    "stable": { "name": "Stable Diffusion", "icon": "🔧", "description": "Keyword-heavy format" },
    "aurora": { "name": "Aurora (xAI)", "icon": "🌅", "description": "Grok's image generation" }
  }
};

function OutfitGenerator() {
  const [generatedOutfits, setGeneratedOutfits] = useState([]);
  const [selectedFormality, setSelectedFormality] = useState([3]);
  const [numberOfOutfits, setNumberOfOutfits] = useState(5);
  const [nsfwMode, setNsfwMode] = useState(false);
  const [selectedAiEngine, setSelectedAiEngine] = useState('chatgpt');
  const [customDetails, setCustomDetails] = useState('');

  const getRandomItem = (array) => array[Math.floor(Math.random() * array.length)];
  
  const getRandomColor = (colorType) => {
    const colorArray = colorsData[colorType] || colorsData.neutral;
    return getRandomItem(colorArray);
  };

  const filterByFormality = (items, allowedLevels) => {
    return items.filter(item => 
      allowedLevels.includes(item.formality) || item.formality === 0 // formality 0 = universal
    );
  };

  const handleFormalityToggle = (level) => {
    if (level === 'random') {
      setSelectedFormality(['random']);
    } else {
      setSelectedFormality(prev => {
        const filtered = prev.filter(f => f !== 'random');
        if (filtered.includes(level)) {
          return filtered.filter(f => f !== level);
        } else {
          return [...filtered, level];
        }
      });
    }
  };

  const getRandomFormality = () => {
    return Math.floor(Math.random() * 5) + 1;
  };

  const formatForAiEngine = (outfit) => {
    const engine = selectedAiEngine;
    const topColor = outfit.pieces.top.color;
    const topItem = outfit.pieces.top.item;
    const bottomColor = outfit.pieces.bottom.color;
    const bottomItem = outfit.pieces.bottom.item;
    const shoeColor = outfit.pieces.shoes.color;
    const shoeItem = outfit.pieces.shoes.item;
    const cleanLocation = outfit.location.replace(/\.$/, '');
    
    const isImageEngine = Object.keys(aiEnginesData.image).includes(engine);
    
    if (isImageEngine) {
      const baseDesc = `beautiful woman wearing ${topColor} ${topItem} and ${bottomColor} ${bottomItem}`;
      const footwear = shoeColor ? `, ${shoeColor} ${shoeItem}` : ', barefoot';
      const setting = cleanLocation.toLowerCase();
      
      switch (engine) {
        case 'midjourney':
          return `${baseDesc}${footwear}, ${setting}, cinematic lighting, professional photography, detailed, high quality --ar 2:3 --style raw`;
        case 'dalle':
          return `A photorealistic image of a ${baseDesc}${footwear}. She is ${setting}. ${outfit.detail}. Professional photography, soft lighting, detailed.`;
        case 'flux':
          return `photorealistic portrait of beautiful woman in ${topColor} ${topItem} and ${bottomColor} ${bottomItem}${footwear}, ${setting}, golden hour lighting, shallow depth of field, 85mm lens, professional photography, highly detailed`;
        case 'stable':
          return `woman, ${topColor} ${topItem}, ${bottomColor} ${bottomItem}${shoeColor ? `, ${shoeColor} ${shoeItem}` : ', barefoot'}, ${setting}, detailed, high quality, professional photography, soft lighting`;
          return `elegant woman in ${topColor} ${topItem} and flowing ${bottomColor} ${bottomItem}${footwear}, ${setting}, warm golden light, dreamy ethereal atmosphere, fine art portrait, soft romantic mood, artistic photography`;
        case 'hidream':
          return `elegant woman in ${topColor} ${topItem} and flowing ${bottomColor} ${bottomItem}${footwear}, ${setting}, warm golden light, dreamy ethereal atmosphere, fine art portrait, soft romantic mood, artistic photography`;
          return `elegant woman in ${topColor} ${topItem} and flowing ${bottomColor} ${bottomItem}${footwear}, ${setting}, warm golden light, dreamy ethereal atmosphere, fine art portrait, soft romantic mood, artistic photography, grok-style creative interpretation`;
          return `woman, ${topColor} ${topItem}, ${bottomColor} ${bottomItem}${shoeColor ? `, ${shoeColor} ${shoeItem}` : ', barefoot'}, ${setting}, detailed, high quality, professional photography, soft lighting`;
        default:
          return `${baseDesc}${footwear}, ${setting}, professional photography`;
      }
    } else {
      switch (engine) {
        case 'claude':
          return outfit.fullDescription;
        case 'chatgpt':
          return `**Setting:** ${cleanLocation}\n**Outfit:**\n• Top: ${topColor} ${topItem}\n• Bottom: ${bottomColor} ${bottomItem}\n• Shoes: ${shoeColor ? `${shoeColor} ${shoeItem}` : shoeItem}\n**Scene:** She ${outfit.action}, ${outfit.detail}.`;
        case 'gemini':
          return `In the golden embrace of ${cleanLocation.toLowerCase()}, she moves with ethereal grace. Adorned in a ${topColor} ${topItem} that catches the light just so, paired with ${bottomColor} ${bottomItem} that flows with her every step. Her ${shoeColor ? `${shoeColor} ${shoeItem}` : 'bare feet'} ${shoeColor ? 'complement' : 'connect her to'} the scene perfectly. ${outfit.action.charAt(0).toUpperCase() + outfit.action.slice(1)}, ${outfit.detail}.`;
        case 'local':
          return `Character: Woman wearing ${topColor} ${topItem}, ${bottomColor} ${bottomItem}, ${shoeColor ? `${shoeColor} ${shoeItem}` : 'barefoot'}. Location: ${cleanLocation}. Action: ${outfit.action}.`;
        default:
          return outfit.fullDescription;
      }
    }
  };

  const generateOutfits = () => {
    const outfits = [];
    
    for (let i = 0; i < numberOfOutfits; i++) {
      let currentFormality;
      let allowedLevels;
      
      if (selectedFormality.includes('random')) {
        currentFormality = getRandomFormality();
        allowedLevels = formalityRulesData[currentFormality];
      } else {
        currentFormality = getRandomItem(selectedFormality);
        allowedLevels = formalityRulesData[currentFormality];
      }
      
      const location = getRandomItem(locationsData[currentFormality] || []);
      
      let availableTops = filterByFormality(clothingData.tops || [], allowedLevels);
      let availableBottoms = filterByFormality(clothingData.bottoms || [], allowedLevels);
      
      if (nsfwMode) {
        availableTops = [...availableTops, ...filterByFormality(nsfwClothingData.tops || [], allowedLevels)];
        availableBottoms = [...availableBottoms, ...filterByFormality(nsfwClothingData.bottoms || [], allowedLevels)];
      }
      
      const availableShoes = filterByFormality(clothingData.shoes || [], allowedLevels);
      
      const selectedTop = getRandomItem(availableTops);
      const selectedBottom = getRandomItem(availableBottoms);
      const selectedShoes = getRandomItem(availableShoes);
      
      const bottomColor = getRandomColor('neutral');
      let topColor;
      
      if (currentFormality <= 2) {
        const colorTypes = ['neutral', 'warm', 'cool', 'vibrant'];
        topColor = getRandomColor(getRandomItem(colorTypes));
      } else if (currentFormality === 3) {
        const colorTypes = ['neutral', 'warm', 'cool'];
        topColor = getRandomColor(getRandomItem(colorTypes));
      } else {
        const colorTypes = ['neutral', 'cool'];
        topColor = getRandomColor(getRandomItem(colorTypes));
      }
      
      const shoeColor = selectedShoes?.item === 'barefoot' ? null : getRandomColor('neutral');
      
      let selectedAction, selectedDetail;
      
      if (nsfwMode) {
        const nsfwActionTypes = ['teasing', 'bold', 'intimate'];
        const regularActionTypes = ['gentle', 'sensual', 'confident'];
        
        if (Math.random() < 0.7) {
          const selectedNsfwType = getRandomItem(nsfwActionTypes);
          selectedAction = getRandomItem(nsfwActionsData[selectedNsfwType] || []);
          selectedDetail = getRandomItem(detailsData.nsfw || []);
        } else {
          const selectedActionType = getRandomItem(regularActionTypes);
          selectedAction = getRandomItem(actionsData[selectedActionType] || []);
          selectedDetail = getRandomItem(detailsData.regular || []);
        }
      } else {
        const actionTypes = ['gentle', 'sensual', 'confident'];
        const selectedActionType = getRandomItem(actionTypes);
        selectedAction = getRandomItem(actionsData[selectedActionType] || []);
        selectedDetail = getRandomItem(detailsData.regular || []);
      }
      
      let outfitDescription = `${topColor?.toLowerCase() || 'black'} ${selectedTop?.item || 'top'}`;
      outfitDescription += `, ${bottomColor?.toLowerCase() || 'black'} ${selectedBottom?.item || 'bottom'}`;
      
      if (selectedShoes?.item !== 'barefoot') {
        outfitDescription += `, ${shoeColor?.toLowerCase() || 'black'} ${selectedShoes?.item || 'shoes'}`;
      } else {
        outfitDescription += `, barefoot`;
      }
      
      const fullDescription = `${location || 'Standing casually'}. Details: ${outfitDescription}. She ${selectedAction || 'poses naturally'}, ${selectedDetail || 'looking confident'}.`;
      
      const finalDescription = customDetails.trim() 
        ? `${fullDescription} ${customDetails.trim()}`
        : fullDescription;

      outfits.push({
        id: i + 1,
        location: location || 'Standing casually',
        outfit: outfitDescription,
        action: selectedAction || 'poses naturally',
        detail: selectedDetail || 'looking confident',
        fullDescription: finalDescription,
        formality: currentFormality,
        pieces: {
          top: { item: selectedTop?.item || 'top', color: topColor || 'black' },
          bottom: { item: selectedBottom?.item || 'bottom', color: bottomColor || 'black' },
          shoes: { item: selectedShoes?.item || 'shoes', color: shoeColor }
        }
      });
    }
    
    const formattedOutfits = outfits.map(outfit => ({
      ...outfit,
      aiFormattedOutput: formatForAiEngine(outfit)
    }));
    
    setGeneratedOutfits(formattedOutfits);
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-pink-50 to-purple-100 p-6">
      <div className="max-w-4xl mx-auto">
        <div className="text-center mb-8">
          <h1 className="text-4xl font-bold text-gray-800 mb-2">✨ Ultimate Outfit Generator ✨</h1>
          <p className="text-gray-600">Generate stunning, coordinated outfits with AI-optimized prompts</p>
        </div>
        
        <div className="bg-white rounded-lg shadow-lg p-6 mb-6">
          <div className="mb-6">
            <label className="block text-sm font-medium text-gray-700 mb-2">
              Content Level
            </label>
            <div className="flex gap-4 mb-4">
              <button
                onClick={() => setNsfwMode(false)}
                className={`px-6 py-3 rounded-lg font-medium transition-colors ${
                  !nsfwMode
                    ? 'bg-blue-600 text-white'
                    : 'bg-gray-200 text-gray-700 hover:bg-gray-300'
                }`}
              >
                🌟 SFW Mode
              </button>
              <button
                onClick={() => setNsfwMode(true)}
                className={`px-6 py-3 rounded-lg font-medium transition-colors ${
                  nsfwMode
                    ? 'bg-red-600 text-white'
                    : 'bg-gray-200 text-gray-700 hover:bg-gray-300'
                }`}
              >
                🔥 NSFW Mode
              </button>
            </div>
            <p className="text-sm text-gray-600">
              {nsfwMode 
                ? '🔥 NSFW: Revealing clothing, bold actions, explicit details'
                : '🌟 SFW: Tasteful outfits with subtle sensual elements'
              }
            </p>
          </div>

          <div className="mb-6">
            <label className="block text-sm font-medium text-gray-700 mb-2">
              Formality Level (Select Multiple)
            </label>
            <div className="flex gap-2 flex-wrap">
              <button
                onClick={() => handleFormalityToggle('random')}
                className={`px-4 py-2 rounded-lg font-medium transition-colors ${
                  selectedFormality.includes('random')
                    ? 'bg-gradient-to-r from-purple-600 to-pink-600 text-white'
                    : 'bg-gray-200 text-gray-700 hover:bg-gray-300'
                }`}
              >
                🎲 Random
              </button>
              {[1, 2, 3, 4, 5].map(level => (
                <button
                  key={level}
                  onClick={() => handleFormalityToggle(level)}
                  disabled={selectedFormality.includes('random')}
                  className={`px-4 py-2 rounded-lg font-medium transition-colors ${
                    selectedFormality.includes(level)
                      ? 'bg-purple-600 text-white'
                      : selectedFormality.includes('random')
                      ? 'bg-gray-100 text-gray-400 cursor-not-allowed'
                      : 'bg-gray-200 text-gray-700 hover:bg-gray-300'
                  }`}
                >
                  {level} - {level === 1 ? 'Beach Casual' : level === 2 ? 'Casual' : level === 3 ? 'Smart Casual' : level === 4 ? 'Business/Evening' : 'Luxury/VIP'}
                </button>
              ))}
            </div>
            <p className="text-xs text-gray-500 mt-1">
              {selectedFormality.includes('random') 
                ? 'Random formality will be chosen for each outfit'
                : `Selected: ${selectedFormality.length === 0 ? 'None' : selectedFormality.join(', ')}`
              }
            </p>
          </div>

          <div className="mb-6">
            <label className="block text-sm font-medium text-gray-700 mb-2">
              ✍️ Custom Details (Optional)
            </label>
            <textarea
              value={customDetails}
              onChange={(e) => setCustomDetails(e.target.value)}
              className="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-purple-500 focus:border-transparent resize-none"
              rows="3"
              placeholder="Add any specific details... (e.g., 'vintage 1950s style, red lipstick, holding martini glass, film noir lighting')"
            />
            <p className="text-xs text-gray-500 mt-1">
              Whatever you type here gets added to every generated outfit description
            </p>
          </div>

          <div className="mb-6">
            <label className="block text-sm font-medium text-gray-700 mb-2">
              Format Prompts For
            </label>
            <div className="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-2">
              {Object.entries(aiEnginesData.text).map(([key, engine]) => (
                <button
                  key={key}
                  onClick={() => setSelectedAiEngine(key)}
                  className={`p-3 rounded-lg text-center transition-colors ${
                    selectedAiEngine === key
                      ? 'bg-indigo-600 text-white'
                      : 'bg-gray-100 hover:bg-gray-200 text-gray-700'
                  }`}
                >
                  <div className="text-lg mb-1">{engine.icon}</div>
                  <div className="text-xs font-medium">{engine.name}</div>
                  <div className="text-xs opacity-75">{engine.description}</div>
                </button>
              ))}
              {Object.entries(aiEnginesData.image).map(([key, engine]) => (
                <button
                  key={key}
                  onClick={() => setSelectedAiEngine(key)}
                  className={`p-3 rounded-lg text-center transition-colors ${
                    selectedAiEngine === key
                      ? 'bg-green-600 text-white'
                      : 'bg-gray-100 hover:bg-gray-200 text-gray-700'
                  }`}
                >
                  <div className="text-lg mb-1">{engine.icon}</div>
                  <div className="text-xs font-medium">{engine.name}</div>
                  <div className="text-xs opacity-75">{engine.description}</div>
                </button>
              ))}
            </div>
          </div>

          <div className="mb-6">
            <label className="block text-sm font-medium text-gray-700 mb-2">
              Number of Outfits
            </label>
            <div className="flex gap-2 flex-wrap">
              {[1, 3, 5, 10, 15, 20].map(num => (
                <button
                  key={num}
                  onClick={() => setNumberOfOutfits(num)}
                  className={`px-4 py-2 rounded-lg font-medium transition-colors ${
                    numberOfOutfits === num
                      ? 'bg-pink-600 text-white'
                      : 'bg-gray-200 text-gray-700 hover:bg-gray-300'
                  }`}
                >
                  {num}
                </button>
              ))}
            </div>
            <input
              type="number"
              min="1"
              max="50"
              value={numberOfOutfits}
              onChange={(e) => setNumberOfOutfits(Math.max(1, Math.min(50, parseInt(e.target.value) || 1)))}
              className="mt-2 w-32 px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-purple-500 focus:border-transparent"
              placeholder="Custom..."
            />
          </div>
          
          <button
            onClick={generateOutfits}
            disabled={selectedFormality.length === 0 && !selectedFormality.includes('random')}
            className={`w-full py-3 px-6 rounded-lg font-medium transition-all transform hover:scale-105 ${
              selectedFormality.length === 0 && !selectedFormality.includes('random')
                ? 'bg-gray-400 text-gray-200 cursor-not-allowed'
                : nsfwMode
                ? 'bg-gradient-to-r from-red-600 to-pink-600 hover:from-red-700 hover:to-pink-700 text-white'
                : 'bg-gradient-to-r from-purple-600 to-blue-600 hover:from-purple-700 hover:to-blue-700 text-white'
            }`}
          >
            {(() => {
              const engineData = aiEnginesData.text[selectedAiEngine] || aiEnginesData.image[selectedAiEngine];
              return engineData ? engineData.icon : '🎲';
            })()} Generate {numberOfOutfits} {nsfwMode ? 'Spicy' : ''} Prompts for {(() => {
              const engineData = aiEnginesData.text[selectedAiEngine] || aiEnginesData.image[selectedAiEngine];
              return engineData ? engineData.name : 'Selected Engine';
            })()}
          </button>
        </div>

        {generatedOutfits.length > 0 && (
          <div className="bg-white rounded-lg shadow-lg p-6">
            <h2 className="text-2xl font-bold text-gray-800 mb-4">
              Generated Prompts for {(() => {
                const engineData = aiEnginesData.text[selectedAiEngine] || aiEnginesData.image[selectedAiEngine];
                return engineData ? `${engineData.icon} ${engineData.name}` : 'Selected Engine';
              })()} ({generatedOutfits.length})
            </h2>
            
            <div className="space-y-6">
              {generatedOutfits.map((outfit) => (
                <div key={outfit.id} className={`border rounded-lg p-4 hover:shadow-md transition-shadow ${
                  nsfwMode ? 'border-red-200 bg-red-50' : 'border-gray-200'
                }`}>
                  <div className="flex justify-between items-start mb-3">
                    <h3 className={`text-lg font-semibold ${nsfwMode ? 'text-red-600' : 'text-purple-600'}`}>
                      {nsfwMode ? '🔥' : '✨'} Prompt #{outfit.id}
                    </h3>
                    <div className="flex gap-2">
                      <span className={`px-2 py-1 rounded-full text-xs font-medium ${
                        nsfwMode ? 'bg-red-100 text-red-800' : 'bg-purple-100 text-purple-800'
                      }`}>
                        Formality {outfit.formality}
                      </span>
                      <span className="bg-indigo-100 text-indigo-800 px-2 py-1 rounded-full text-xs font-medium">
                        {(() => {
                          const engineData = aiEnginesData.text[selectedAiEngine] || aiEnginesData.image[selectedAiEngine];
                          return engineData ? `${engineData.icon} ${engineData.name}` : 'Selected Engine';
                        })()}
                      </span>
                    </div>
                  </div>
                  
                  <div className="grid md:grid-cols-2 gap-4">
                    <div>
                      <h4 className="text-sm font-semibold text-gray-600 mb-1">📍 Location</h4>
                      <p className="text-gray-700 text-sm mb-3">{outfit.location}</p>
                      
                      <h4 className="text-sm font-semibold text-gray-600 mb-1">👗 Outfit</h4>
                      <div className="text-sm space-y-1">
                        <div className="flex justify-between">
                          <span>Top:</span>
                          <span className="capitalize font-medium">{outfit.pieces.top.color} {outfit.pieces.top.item}</span>
                        </div>
                        <div className="flex justify-between">
                          <span>Bottom:</span>
                          <span className="capitalize font-medium">{outfit.pieces.bottom.color} {outfit.pieces.bottom.item}</span>
                        </div>
                        <div className="flex justify-between">
                          <span>Shoes:</span>
                          <span className="capitalize font-medium">
                            {outfit.pieces.shoes.color ? 
                              `${outfit.pieces.shoes.color} ${outfit.pieces.shoes.item}` : 
                              outfit.pieces.shoes.item
                            }
                          </span>
                        </div>
                      </div>
                    </div>
                    
                    <div>
                      <h4 className="text-sm font-semibold text-gray-600 mb-1">
                        {(() => {
                          const engineData = aiEnginesData.text[selectedAiEngine] || aiEnginesData.image[selectedAiEngine];
                          const isImageEngine = Object.keys(aiEnginesData.image).includes(selectedAiEngine);
                          return engineData ? `${engineData.icon} ${isImageEngine ? 'AI Image Prompt' : 'Formatted Output'}` : 'Output';
                        })()}
                      </h4>
                      <div className={`p-3 rounded-lg ${
                        nsfwMode ? 'bg-gradient-to-r from-red-50 to-pink-50' : 'bg-gradient-to-r from-purple-50 to-pink-50'
                      }`}>
                        <p className="text-gray-800 text-sm leading-relaxed font-mono">
                          {outfit.aiFormattedOutput}
                        </p>
                        <button
                          onClick={() => navigator.clipboard.writeText(outfit.aiFormattedOutput)}
                          className="mt-2 text-xs text-indigo-600 hover:text-indigo-800 transition-colors"
                        >
                          📋 Copy to Clipboard
                        </button>
                      </div>
                    </div>
                  </div>
                </div>
              ))}
            </div>
            
            <div className="mt-6 text-center">
              <button
                onClick={generateOutfits}
                className={`px-6 py-2 rounded-lg font-medium transition-all ${
                  nsfwMode
                    ? 'bg-gradient-to-r from-red-500 to-pink-500 hover:from-red-600 hover:to-pink-600 text-white'
                    : 'bg-gradient-to-r from-pink-500 to-purple-500 hover:from-pink-600 hover:to-purple-600 text-white'
                }`}
              >
                🔄 Generate {numberOfOutfits} More for {(() => {
                  const engineData = aiEnginesData.text[selectedAiEngine] || aiEnginesData.image[selectedAiEngine];
                  return engineData ? engineData.name : 'Selected Engine';
                })()}
              </button>
            </div>

            {/* Premium Image Generation Upsell */}
            <div className="mt-8 p-6 bg-gradient-to-r from-purple-50 to-pink-50 rounded-lg border-2 border-dashed border-purple-200">
              <div className="text-center">
                <h3 className="text-xl font-bold text-gray-800 mb-2">🎨 Want to See These as Actual Images?</h3>
                <p className="text-gray-600 mb-4">
                  Don't just imagine your outfits - see them come to life! We'll create high-quality images for you.
                </p>
                
                <div className="grid md:grid-cols-3 gap-4 mb-6">
                  <div className="bg-white p-4 rounded-lg shadow-sm">
                    <div className="text-2xl mb-2">⚡</div>
                    <h4 className="font-medium text-gray-800 mb-1">Fast Generation</h4>
                    <p className="text-sm text-gray-600">Images ready in under 60 seconds</p>
                  </div>
                  <div className="bg-white p-4 rounded-lg shadow-sm">
                    <div className="text-2xl mb-2">🎯</div>
                    <h4 className="font-medium text-gray-800 mb-1">Perfect Quality</h4>
                    <p className="text-sm text-gray-600">Professional-grade AI generation</p>
                  </div>
                  <div className="bg-white p-4 rounded-lg shadow-sm">
                    <div className="text-2xl mb-2">💾</div>
                    <h4 className="font-medium text-gray-800 mb-1">Instant Download</h4>
                    <p className="text-sm text-gray-600">High-res files delivered immediately</p>
                  </div>
                </div>

                <div className="bg-white p-4 rounded-lg shadow-sm mb-4">
                  <div className="text-lg font-bold text-purple-600 mb-1">
                    Only $0.015 per image
                  </div>
                  <div className="text-sm text-gray-600">
                    {numberOfOutfits} images = ${(numberOfOutfits * 0.015).toFixed(3)} • Add $1 in tokens to get started
                  </div>
                </div>

                <button className="bg-gradient-to-r from-purple-600 to-pink-600 text-white px-8 py-3 rounded-lg font-medium hover:from-purple-700 hover:to-pink-700 transition-all transform hover:scale-105 shadow-lg">
                  🎨 Generate {numberOfOutfits} Images (${(numberOfOutfits * 0.015).toFixed(3)})
                </button>
              </div>
            </div>
          </div>
        )}
        
        <div className="mt-8 text-center text-gray-600 text-sm">
          <p>🔥 Cross-platform AI outfit generation with JSON-driven content 🔥</p>
        </div>
      </div>
    </div>
  );
}

export default OutfitGenerator;
