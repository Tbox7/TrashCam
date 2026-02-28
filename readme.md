## Inspiration
While researching ideas for this hackathon we came across a stat that shows we can reduce landfill waste by 60-70% if we properly split trash, recycle, and compost. So we decided to create an application that uses CV to help with categorization. 
## What it does
You can use this application to help you accurately discard of your garbage. Using a camera, the application uses a classification model to identify the item and another model to determine which category it belongs to. It also stores all the trash, recycle, and compost items so you can see how much of each you have thrown away. 
## How we built it
TrashCam is a Python desktop app that uses your webcam to analyze only the item inside a green on-screen box, continuously predicts the item with google/vit-base-patch16-224, and when you click Classify it predicts the disposal category (recycle, compost, or landfill) from the ROI image using openai/clip-vit-large-patch14 (or, if you manually type an item name, it uses all-mpnet-base-v2 from SentenceTransformers as a text-similarity fallback), then lets you choose Next (Save) to log the confirmed result to a local SQLite database or Redo to discard it, with a Reports tab that summarizes category totals between two selected dates.
## Schema
<img width="3740" height="1727" alt="Schematics" src="https://github.com/user-attachments/assets/061ce503-77ee-4b92-9171-8a208bd6ef8c" />

## Challenges we ran into
The main challenge we ran into was balancing computational power and accurate results. It was a lot of trial and error to see which model was both light and accurate. We ran into problems where models that were easy to run had a large number of incorrect classifications and large accurate models took a long time to produce results. Ultimately, we decided to use openai's clip model, as it balances being both lightweight and accurate.  
## Accomplishments that we're proud of
Having entered the hackathon with only a couple days left, we are happy to have taken an idea and submit something that works just as we wanted it too. Through this project, we learnt a lot more about our planet and how even our small actions like choosing whether to recycle, compost, or trash our garbage, can compound into lasting effects. 
## What we learned
As mentioned above we did not have much time to complete our idea. We had to learn to break tasks down, split them fairly, sync our workflows, and a lot more about project management. Though our final submission does not include any API's, through the development phase we did experiment with and learn how to work with them. 
## Known Limitations
- Camera Dependencies: lighting, blur, occlusion, reflections, and background clutter can affect accuracy. 
- No Material Chemistry Understanding: model cannot see contamination, coating types, food residue level, etc, which can all affect categorization. 
- Uses Umbrella Generalization: Model generalizes as all items as the same, ie: not all pens are recyclable, but model categorizes it as such.  
## What's next for TrashCam
- Reduce computational time
- A more comprehensible report with charts and graphs
- Fun messages to show progress; such as but not limited to metaphors, similes, equivalencies, etc.
