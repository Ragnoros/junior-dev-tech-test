## Carter Changes

<h2>Bugs</h2>
Bug 1:<br>
Added a semi colon to the end of line 29 in App.vue file
<br>
<br>
Bug 2:<br>
Added closing quotes and a comma to the end of line 60 in product.json
Added closing quotes on line 61 just after "width" in product.json
<br>
<br>
Bug 3: ? (I assume it's the 3rd bug)<br>
Changed line 9 inside the quotes in product.vue to "../components/data/product.json"
<br>
<br>
Small changes:<br>
Added height and width to line 49 and 50 in product.json. don't know if i was supposed to but found it off how it didnt have dimensions like other images.

<h2>Coding walkthrough / reasoning:</h2>
<h4>Page Layout</h4>
I opted to split the page in 2. using d-flex and flex wrap with a min width of 300px so rather than keep shrinking when the page becomes thinner the info panel drops below the gallery when small enough creating a responsive feel<br>
<br></br>

    <div id="img-panel" class="border-0 text-start ms-5" style="flex: 2; min-width: 300px">
    <div id="info-panel" class="text-end pe-5" style="flex: 1; min-width: 300px; margin-left: auto">

<h4>Info-Panel</h4>
For the offer label I decided to create a single border on the left and tried to match the colour as best as possible on the design spec. I imported the poppins css file and applied 'poppins-light'. 
The title and colour were placed inside the same p tag seperated by a bar |.<br>
<br>
In the price reduction section I used bootstrap table which was extremely convenient and gave me an easy way to put the prices below 'Original' and 'Now'. I originally calculated the percentage inside the template tags but in my opinion this was messy so I did the calculation in the data function and created a new data property.<br>
<br>
Inside the alt colours section I decided to create another data property inside the data function. When rendering I originally went for an unordered list but realised this was not responsive and instead used the bootstrap grid/container which made it much better. I commented out the old code rather than delete it to show my learning progress. I counted through the list using the v-for directive which is extremely convenient for rendering list items.<br>
<br>
On the sizes I did the same as alt colours. I created a new data propertly for the list objects and then originally counted through an unordered list but quickly realised it was not fit for purpose not only on the responsive side but these sizes needed to be toggled to select a size. I opted to render a list of buttons that could be toggled on and off but all buttons could be selected at the same time. This lead me to the bootstrap radio buttons.

           <div class="col" v-for="(size, index) in sizes" key="index">
              <input
                type="radio"
                class="btn-check"
                name="options"
                :id="`option${index + 1}`"
                autocomplete="off"
                checked
                :value="size"
                v-model="selectedSize"
              />
              <label
                class="btn btn-outline-dark rounded-0 custom-border"
                :for="`option${index + 1}`"
                >{{ size }}</label
              >

In the above snipet I used template literals inside the id of the Input tag to use the index to increase the option number because each of these buttons needed an id of option1, option2 etc, this allowed me to render the sizes dynamically rather than statically typing them out. I incremented each index by 1, otherwise the first id would be option0 which I don't think would work but i've not actually tested it.<br>
I added size to :value to bind it when selecting a size. v-model then bound whatever the value was to selectedSize in the data function.
<br>
<br>
The 'Add To Bag' button renders a bootstrap modal, the button is disabled while selectedSize is null in the hope that it avoids errors in the future. once this modal opens it grabs an image, title and the selectedSize. These 3 datapoints are then displayed inside the modal with a button to 'continue shopping' and 'go to bag'. Both buttons are pill shaped to match the 'add to bag' button.
<br>
<br>
The description section is a P tag which displays the text. The bullet points are also in a P tag but in a v-html vue directive so that the html inside the string renders properly `<p v-html="product.product_bulletpoints"></p>`

<h4>Img-Panel</h4>
I created a new data property again for the gallery. I counted through the gallery list in a grid container with a v-for directive and rendered them onto the page.

<h2>Possible Changes:</h2>

I think the sizes could be turned into a drop down, this could potentially make it better for responsivnes. <br>
<br>
Possibly condense the description section and bullet points into a drop down.
