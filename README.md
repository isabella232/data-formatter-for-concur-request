<img src="./media/image1.png" style="width:2.26389in;height:0.41667in" />

<h1 align="center">Data Formatter for Concur Request</h1>

This file has been created to assist TMCs with documenting proposals
back to a GDS Container PNR as part of the Agency Proposal Powered by
Compleat flow.

This file will ensure accuracy when entering the remark lines into the
GDS Container PNR and help provide all the mandatory elements to Travel
Request

# CONFIGURATION

The “Data Formatter for Concur Request” file has been programmed to
perform a concatenation of the remarks generated to allow for more than
one remark line to be copied at a time.

**The remarks order must be respected in order to have a successful PNR
transmission to Request.**

The configuration for the concatenation varies depending on the tool
used to interact with the GDS and the GDS itself. We have therefore
allowed for updates to the concatenation character and the number of
instances in the output block.

For more information on concatenation use and output examples, please
see the [Concatenation](#concatenation) section below.

Prior to implementation, please determine the correct character and
instances for your tool and GDS.

To edit the character and instances:

-   Save the file

-   Right click the file, and “open with” any document editor.

You will see the following at the beginning of the document:

/\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\* Concatenation Variables
\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*/

// Concatenation Characters for each gds

concatStringApollo = "+"

concatStringAmadeus = ";"

concatStringGalileo = "+"

concatStringSabre = "&"

concatStringWorldspan = "#"

// Number of Concatenations for each Gds

lineLimitApollo = 8

lineLimitAmadeus = 8

lineLimitGalileo = 28

lineLimitSabre = 79

lineLimitWorldspan = 80

-   To update the character, amend the concatString value inside " "

-   To amend the number of concatenation instances, amend the lineLimit
    value after =\[space\]

-   Save the changes

-   Test the output against your GDS interaction tool, ensuring that the
    maximum value of instances is achieved

# GENERAL TAB 

This tab is used to add mandatory information remarks to the GDS
Container PNR.

This will be the landing page when the file is opened.

N.B. This document uses Apollo remark examples only.

## General Tab completion flow

## General Tab screenshot example

<img src="./media/image3.png" style="width:7.28358in;height:3.36112in" />

This step must be performed for each proposal before adding the related
segment remark data into the PNR.

## General Tab table of definitions

### General Tab mandatory information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 21%" />
<col style="width: 28%" />
</colgroup>
<thead>
<tr class="header">
<th><p>File input</p>
<p>and description</p></th>
<th>PNR Remark label</th>
<th>PNR Remark example</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>(1) Locator</p>
<p>This is the record locator of the container PNR that the customer will use in any communication.</p>
<p>It can be either the GDS Container PNR locator or the locator of an additional booking.</p></td>
<td>LOC-</td>
<td>LOC-2NCMIA</td>
</tr>
<tr class="even">
<td><p>(2) Select a GDS</p>
<p>This is where you choose the GDS (in our example Apollo) needed to generate the Container PNR.</p></td>
<td>Drop down choice on file</td>
<td>@:5P/APTR…</td>
</tr>
<tr class="odd">
<td><p>(3) Select a Proposal Number</p>
<p>This is where you select the proposal number (3 is the maximum).</p>
<p>Each proposal must be entered in turn. After each is completed (and copied and pasted) the data for the next proposal can be updated.</p></td>
<td>PROP1</td>
<td>@:5P/APTR/54/PROP1/…</td>
</tr>
<tr class="even">
<td><p>(4) General</p>
<p>This tab is used to fill in the general information that is needed for the GDS Container PNR.</p></td>
<td>GEN</td>
<td>@:5P/APTR/54/PROP1/GEN/…</td>
</tr>
</tbody>
</table>

### 

***  
***

### General Tab optional information

<table>
<colgroup>
<col style="width: 54%" />
<col style="width: 19%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>File input</p>
<p>and description</p></th>
<th>PNR Remark label</th>
<th><p>PNR Remark example</p>
<p>with default values</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Proposal Expiry Date</p>
<p>This is the expiry date and time of the proposal.</p>
<ul>
<li><p>Date is in the format DD/MMM/YYYY</p></li>
<li><p>Time is in the format HHMM and is 24 hours</p></li>
</ul></td>
<td><p>LIMIT-</p>
<p>T-</p></td>
<td><p>LIMIT-2021-06-30</p>
<p>T102500.000</p>
<p>(shows as LIMIT-/ if blank)</p></td>
</tr>
<tr class="even">
<td><p>Agency Branch Offset to GMT/UTC</p>
<p>This is the agency branch time zone.</p>
<p>This works in conjunction with the Proposal Expiry so that the correct time can be applied adjusting any offset.</p>
<p>Select if the Offset is MINUS or PLUS GMT/UTC</p>
<ul>
<li><p>Date is in the format DD/MMM/YYYY</p></li>
<li><p>Time is in the format HHMM and is 24 hours</p></li>
</ul></td>
<td>ZPLUS</td>
<td><p>ZPLUS0000</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Remarks</p>
<p>This is a free text field for any additional information.</p></td>
<td>RMKS-</td>
<td><p>RMKS-GENERAL TAB COMMENTS FREE TEXT</p>
<p>(shows as RMKS-/ if blank)</p></td>
</tr>
<tr class="even">
<td><p>Booked</p>
<p>Select this option if you have pre-booked a proposal for policy compliance reasons. This will be shown to the traveller in the next version of Agency Proposal user interface v2.</p>
<p>The default is unchecked</p></td>
<td>BKD-</td>
<td><p>BKD-FALSE</p>
<p>(default value)</p></td>
</tr>
</tbody>
</table>

## AIR TAB

This is where you complete the details for a single or return air
segment.

### Air Tab completion flow for one-way

### Air Tab one-way screenshot example

<img src="./media/image4.png" style="width:6.69375in;height:3.33333in" />

## Air Tab one-way table of definitions 

### Air Tab one-way mandatory information

<table>
<colgroup>
<col style="width: 51%" />
<col style="width: 20%" />
<col style="width: 28%" />
</colgroup>
<thead>
<tr class="header">
<th><p>File input</p>
<p>and description</p></th>
<th>PNR Remark label</th>
<th>PNR Remark example</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AIR – One Way</p>
<p>This is the Air segment tab to fill in the information for</p></td>
<td>SEG-</td>
<td>SEG-AIR1</td>
</tr>
<tr class="even">
<td><p>(1) Currency</p>
<p>This is the three-letter ISO standard code for the currency used. For example: GBP, EUR…</p></td>
<td>CURR-</td>
<td>CURR-GBP</td>
</tr>
<tr class="odd">
<td><p>(2) Fare</p>
<p>This is the total amount of the Air segment.</p>
<p>It will automatically format to 2 decimal places if not typed.</p>
<p>We currently only support decimalized currencies</p></td>
<td>VAL-</td>
<td>VAL-215.00</td>
</tr>
<tr class="even">
<td><p>(3) Departure IATA</p>
<p>This is the three-letter IATA airport code for the departure.</p></td>
<td>IATA</td>
<td>IATA-LHR</td>
</tr>
<tr class="odd">
<td><p>(4) Arrival IATA</p>
<p>This is the three-letter IATA airport code for the arrival.</p></td>
<td>IATA</td>
<td>IATA-CDG</td>
</tr>
<tr class="even">
<td><p>(5) Flight Number</p>
<p>This is the flight number and should be:</p>
<p>the airline two-letter IATA code followed by the flight number</p></td>
<td>FN-</td>
<td>FN-BA258</td>
</tr>
<tr class="odd">
<td><p>Confirmation Number</p>
<p>This is where you will add the provider reference if you have selected “Booked”.</p>
<p>This is only mandatory when Booked is checked</p></td>
<td>CONF-</td>
<td><p>CONF-ABCDEF</p>
<p>CONF-NA</p>
<p>(default value if blank)</p></td>
</tr>
<tr class="even">
<td><p>(6) Departure Date and Time</p>
<p>(7) Arrival Date and Time</p>
<p>This should be entered using the following format:</p>
<ul>
<li><p>Date is in the format DD/MMM/YYYY</p></li>
<li><p>Time is in the format HHMM and is 24 hours</p></li>
</ul></td>
<td>DTE-…/AT-</td>
<td><p>DTE-2021-09-07/AT-0920</p>
<p>DTE-2021-09-07/AT-0930</p></td>
</tr>
<tr class="odd">
<td><p>(8) Airline Class</p>
<p>This is the cabin class description in full.</p></td>
<td>C-</td>
<td>C-ECONOMY</td>
</tr>
</tbody>
</table>

### Air Tab one-way optional information

<table>
<colgroup>
<col style="width: 52%" />
<col style="width: 19%" />
<col style="width: 27%" />
</colgroup>
<thead>
<tr class="header">
<th><p>File input</p>
<p>and description</p></th>
<th>PNR Remark label</th>
<th>PNR Remark example</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Booked</p>
<p>Select this if the flight is booked (eg low-cost carrier).</p></td>
<td>BKD-</td>
<td><p>BKD-TRUE</p>
<p>or</p>
<p>BKD-FALSE</p>
<p>(default value)</p></td>
</tr>
<tr class="even">
<td><p>Confirmation Number</p>
<p>This is where you will add the provider reference if applicable.</p>
<p>This is optional when “Booked” is not selected.</p></td>
<td>CONF-</td>
<td><p>CONF-ABCDEF</p>
<p>CONF-NA</p>
<p>(default value if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Flight Duration</p>
<p>This is the flight duration information in minutes.</p></td>
<td>DUR-</td>
<td><p>DUR-150</p>
<p>(shows as DUR-/ if blank)</p></td>
</tr>
<tr class="even">
<td><p>Departure Terminal</p>
<p>This is where you add the departure terminal information.</p></td>
<td>TD-</td>
<td><p>TD-NORTH</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Arrival Terminal</p>
<p>This is where you add the arrival terminal information.</p></td>
<td>TA-</td>
<td><p>TA-SOUTH</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Policy Compliance Level(%)</p>
<p>This will be a value between 0-100 that matches the segment compliance (100 if fully compliant and 0 if not compliant at all).</p></td>
<td>LVL-</td>
<td><p>LVL-85</p>
<p>(shows as LVL-/ if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Comments</p>
<p>This is where any additional comments related to the air segment can be added.</p>
<p>For example, the fare conditions or any information that you want to pass to the traveller. It is free text.</p></td>
<td>RMKS-</td>
<td><p>RMKS-ONE WAY TEST</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Meals</p>
<p>This is where you add the meal information, ideally using the meal code. In our example, it is a vegetarian meal.</p></td>
<td>MEAL-</td>
<td><p>MEAL-VGML</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Seat Number</p>
<p>This is where you add the seat number. It is free text.</p></td>
<td>SEAT-</td>
<td><p>SEAT-2C</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Equipment</p>
<p>This is where you add the equipment information if available.</p></td>
<td>EQP-</td>
<td><p>EQP-757</p>
<p>(not shown if blank)</p></td>
</tr>
</tbody>
</table>

## Air Tab completion flow for round trip

## Air Tab round trip screenshot examples

### Air Tab round trip input display 

<img src="./media/image5.png" style="width:7.08209in;height:2.84268in" />

### Air Tab round trip output display

<img src="./media/image6.png" style="width:7.09694in;height:3.29851in" />

## Air Tab round trip table of definitions

### Air Tab round trip mandatory information 

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 16%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>File input</p>
<p>and description</p></th>
<th>PNR Remark label</th>
<th>PNR Remark examples</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AIR – Round Trip</p>
<p>This is the tab you are working on and the segment type.</p></td>
<td>SEG-</td>
<td><p>SEG-AIR1</p>
<p>SEG-AIR2</p></td>
</tr>
<tr class="even">
<td><p>(1) Currency</p>
<p>This is the three letter ISO standard code for the currency used for example: GBP, EUR, USD</p></td>
<td>CURR-</td>
<td>CURR-GBP</td>
</tr>
<tr class="odd">
<td><p>(2) Fare</p>
<p>This is the total amount of the Air segment.</p>
<p>It will automatically format to 2 decimal places if not typed.</p>
<p>We currently only support decimalized currencies</p></td>
<td>VAL-</td>
<td>VAL-215.00</td>
</tr>
<tr class="even">
<td><p>(3) Departure IATA</p>
<p>This is the IATA three-letter airport code for the departure.</p></td>
<td>IATA</td>
<td>IATA-LHR</td>
</tr>
<tr class="odd">
<td><p>(4) Arrival IATA</p>
<p>This is the IATA three-letter airport code for the arrival.</p></td>
<td>IATA</td>
<td>IATA-CDG</td>
</tr>
<tr class="even">
<td><p>(5) Flight Number</p>
<p>This is the flight number and should be:</p>
<p>the airline two-letter IATA code followed by the flight number</p></td>
<td>FN-</td>
<td>FN-BA258</td>
</tr>
<tr class="odd">
<td><p>(6) Confirmation Number</p>
<p>This is where you will add the provider reference if you have selected “Booked”.</p>
<p>This is only mandatory when Booked is checked</p></td>
<td>CONF-</td>
<td><p>CONF-ABCDEF</p>
<p>CONF-NA</p>
<p>(default value if blank)</p></td>
</tr>
<tr class="even">
<td><p>(7) Departure Date and Time</p>
<p>(8) Arrival Date and Time</p>
<p>This is the departure and or arrival date and time with the following format:</p>
<ul>
<li><p>Date is in the format DD/MMM/YYYY</p></li>
<li><p>Time is in the format HHMM and is 24 hours</p></li>
</ul></td>
<td>DTE-…/AT-</td>
<td><p>DTE-2021-06-30/AT-0920</p>
<p>DTE-2021-06-30/AT-0920</p></td>
</tr>
<tr class="odd">
<td><p>(9) Airline Class</p>
<p>This is the cabin class description in full, not just the letter.</p></td>
<td>C-</td>
<td>C-ECONOMY</td>
</tr>
<tr class="even">
<td><p>(10) Return Departure Date and Time</p>
<p>(11) Return Arrival Date and Time</p>
<p>This is the return departure date using the following format:</p>
<ul>
<li><p>Date is in the format DD/MMM/YYYY</p></li>
<li><p>Time is in the format HHMM and is 24 hours</p></li>
</ul></td>
<td>DTE-…/AT-</td>
<td><p>SEG-AIR2/DTE-2021-07-05/AT-0750</p>
<p>SEG-AIR2/DTE-2021-07-05/AT-0830</p></td>
</tr>
<tr class="odd">
<td><p>(12) Return Flight Number</p>
<p>This is the return flight number and should be:</p>
<p>the airline two-letter IATA code followed by the flight number</p></td>
<td>FN-</td>
<td>FN-AF412</td>
</tr>
<tr class="even">
<td><p>(13) Return Airline Class</p>
<p>This is the return cabin class description in full.</p></td>
<td>C-</td>
<td>SEG-AIR2/C-BUSINESS</td>
</tr>
</tbody>
</table>

### 

***  
***

### Air Tab round trip optional information 

<table>
<colgroup>
<col style="width: 53%" />
<col style="width: 15%" />
<col style="width: 31%" />
</colgroup>
<thead>
<tr class="header">
<th><p>File input</p>
<p>and description</p></th>
<th>PNR Remark label</th>
<th>PNR Remark example</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Booked</p>
<p>Select this if the flight you are detailing is booked (eg: low-cost carrier).</p></td>
<td>BKD-</td>
<td><p>BKD-FALSE</p>
<p>(default value)</p></td>
</tr>
<tr class="even">
<td><p>Confirmation Number</p>
<p>This is where you will add the provider reference if applicable.</p>
<p>This is optional when “Booked” is not selected.</p></td>
<td>CONF-</td>
<td><p>CONF-ABCDEF</p>
<p>CONF-NA</p>
<p>(default value if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Flight Duration</p>
<p>This is for the flight duration information in minutes.</p></td>
<td>DUR-</td>
<td><p>DUR-150</p>
<p>(shows as DUR-/ if blank)</p></td>
</tr>
<tr class="even">
<td><p>Departure Terminal</p>
<p>This is where you add the departure terminal information.</p></td>
<td>TD-</td>
<td><p>TD-NORTH</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Arrival Terminal</p>
<p>This is where you add the arrival terminal information.</p></td>
<td>TA-</td>
<td><p>TA-SOUTH</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Policy Compliance Level(%)</p>
<p>This will be a value between 0-100 that matches the segment compliance (100 if fully compliant and 0 if not compliant at all).</p></td>
<td>LVL-</td>
<td><p>LVL-85</p>
<p>(shows as LVL-/ if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Comments</p>
<p>This is where any additional comments related to the air segment can be added as free text.</p>
<p>For example, the fare conditions or any information that you want to pass to the traveler.</p></td>
<td>RMKS-</td>
<td><p>RMKS-ONE WAY TEST</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Meals</p>
<p>This is where you add the meal information. It should be entered as the meal code. In our example, it is a vegetarian meal.</p></td>
<td>MEAL-</td>
<td><p>MEAL-VGML</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Seat Number</p>
<p>This is where you add the seat number. It is free text.</p></td>
<td>SEAT-</td>
<td><p>SEAT-2C</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Equipment</p>
<p>This is where you add the equipment information if required.</p></td>
<td>EQP-</td>
<td><p>EQP-757</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Return Duration</p>
<p>This is the return flight duration in minutes.</p></td>
<td>DUR-</td>
<td><p>DUR-180</p>
<p>(shows as DUR-/ if blank)</p></td>
</tr>
<tr class="even">
<td><p>Return Seat Number</p>
<p>This is where you enter the seat number for the inbound flight.</p></td>
<td>SEAT-</td>
<td><p>SEAT-3A</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Return Meals</p>
<p>This is where you add the meal information for the inbound flight. It should be entered as the meal code. In our example, it is a vegetarian meal.</p></td>
<td>MEAL-</td>
<td><p>MEAL-VGML</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Return Equipment</p>
<p>This is where you can add the equipment information for the inbound flight.</p></td>
<td>EQP-</td>
<td><p>EQP-744</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Return Departure Terminal</p>
<p>This is where you give the departure terminal information.</p></td>
<td>TD-</td>
<td><p>TD-F</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Return Arrival Terminal</p>
<p>This is where you give the arrival terminal information.</p></td>
<td>TA-</td>
<td><p>TA-NORTH</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Return Comments</p>
<p>This is where any additional comments can be added.</p>
<p>For example, the fare conditions.</p></td>
<td>RMKS-</td>
<td><p>RMKS-AIR COMMENT FOR THE INBOUND LEG AND COULD BE USED FOR FARE CONDITIONS TOO</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Return Policy Compliance Level(%)</p>
<p>This will be a value between 0-100 that matches the segment compliance (100 if fully compliant and 0 if not compliant at all) for the inbound flight.</p></td>
<td>LVL-</td>
<td><p>LVL-85</p>
<p>(shows as LVL-/ if blank)</p></td>
</tr>
</tbody>
</table>

## CAR TAB

This is where all the details regarding the information for a Car
segment should be added.

## Car Tab completion flow

## Car Tab screenshot example

<img src="./media/image7.png" style="width:6.69375in;height:2.95237in" />

## Car Tab table of definitions 

### Car Tab mandatory information

<table>
<colgroup>
<col style="width: 49%" />
<col style="width: 20%" />
<col style="width: 30%" />
</colgroup>
<thead>
<tr class="header">
<th><p>File input</p>
<p>and description</p></th>
<th>PNR Remark label</th>
<th>PNR Remark examples</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CAR</p>
<p>This is the tab and the segment type.</p></td>
<td>SEG-</td>
<td>SEG-CAR</td>
</tr>
<tr class="even">
<td><p>(1) Pickup Country Code</p>
<p>This is the pickup two-letter IATA country code.</p></td>
<td>CO-</td>
<td>CO-FR</td>
</tr>
<tr class="odd">
<td><p>(2) Pickup City</p>
<p>This is the pickup city name in full.</p></td>
<td>CITY-</td>
<td>CITY-PARIS</td>
</tr>
<tr class="even">
<td><p>(3) Pickup Details</p>
<p>This is where you enter the details about the pickup.</p></td>
<td>NOTE-</td>
<td>NOTE-RAIL STATION</td>
</tr>
<tr class="odd">
<td><p>(4) Confirmation Number</p>
<p>This is where you will add the provider reference if you have selected “Booked”.</p>
<p>This is only mandatory when “Booked” is checked</p></td>
<td>CONF-</td>
<td><p>CONF-ABCDEF</p>
<p>CONF-NA</p>
<p>(default value if blank)</p></td>
</tr>
<tr class="even">
<td><p>(5) Drop Off Country Code</p>
<p>This is the drop off two-letter IATA country code.</p></td>
<td>CO-</td>
<td>CO-FR</td>
</tr>
<tr class="odd">
<td><p>(6) Drop Off City</p>
<p>This is the drop off city name in full.</p></td>
<td>CITY-</td>
<td>CITY-LYON</td>
</tr>
<tr class="even">
<td><p>(7) Supplier Name</p>
<p>This is the supplier name in full.</p></td>
<td>SUP-</td>
<td>SUP-AVIS</td>
</tr>
<tr class="odd">
<td><p>(8) Pickup Date and Time</p>
<p>This is the pickup date and time using the following format:</p>
<ul>
<li><p>Date is in the format DD/MMM/YYYY</p></li>
<li><p>Time is in the format HHMM and is 24 hours</p></li>
</ul></td>
<td>DTE-…/AT-…</td>
<td>DTE-2021-06-19/AT-1000</td>
</tr>
<tr class="even">
<td><p>(9) Drop Off Date and Time</p>
<p>This is the drop off date and time using the following format:</p>
<ul>
<li><p>Date is in the format DD/MMM/YYYY</p></li>
<li><p>Time is in the format HHMM and is 24 hours</p></li>
</ul></td>
<td>DTE-…/AT-…</td>
<td>DTE-2021-06-22/AT-0730</td>
</tr>
<tr class="odd">
<td><p>(10) Currency</p>
<p>This is the three-letter ISO standard code for the currency used. For example: GBP, EUR, USD…</p></td>
<td>CURR-</td>
<td>CURR-EUR</td>
</tr>
<tr class="even">
<td><p>(11) Rate</p>
<p>This is the total amount of the Car segment.</p>
<p>It will automatically format to 2 decimal places if not typed.</p>
<p>We currently only support decimalized currencies.</p></td>
<td>VAL-</td>
<td>VAL-150.00</td>
</tr>
</tbody>
</table>

### Car Tab optional information

<table>
<colgroup>
<col style="width: 46%" />
<col style="width: 19%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>File input</p>
<p>and description</p></th>
<th>PNR Remark label</th>
<th><p>PNR Remark examples</p>
<p>with default values</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Booked</p>
<p>If you have booked the car and selected this field, the “Confirmation Number” will become mandatory.</p></td>
<td>BKD-</td>
<td><p>BKD-TRUE</p>
<p>or</p>
<p>BKD-FALSE</p>
<p>(default value)</p></td>
</tr>
<tr class="even">
<td><p>Confirmation Number</p>
<p>This is where you enter the booking reference obtained from the provider if applicable.</p>
<p>This is optional when “Booked” is not selected.</p></td>
<td>CONF-</td>
<td><p>CONF-14545</p>
<p>or</p>
<p>CONF-NA</p>
<p>(default value)</p></td>
</tr>
<tr class="odd">
<td><p>Pickup IATA</p>
<p>This is the three-letter city code of the pickup city.</p></td>
<td>IATA-</td>
<td><p>IATA-PAR</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Drop Off Details</p>
<p>This is where you can add any information regarding the drop off.</p></td>
<td>NOTE-</td>
<td><p>NOTE-AT HILTON RECEPTION</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Drop Off IATA</p>
<p>This is the three-letter city code of the drop off city.</p></td>
<td>IATA-</td>
<td><p>IATA-LYS</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Class</p>
<p>This is where you add the car category in full.</p></td>
<td>C-</td>
<td><p>C-COMPACT</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Policy Compliance Level (%)</p>
<p>This will be a value between 0-100 that matches the segment compliance (100 if fully compliant and 0 if not compliant at all).</p></td>
<td>LVL-</td>
<td><p>LVL-100</p>
<p>(shows as LVL-/ if blank)</p></td>
</tr>
<tr class="even">
<td><p>Comments</p>
<p>This is where you can add any free text additional information regarding the car segment.</p></td>
<td>RMKS-</td>
<td><p>RMKS-CAR COMMENT EXAMPLE</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Transmission Preference</p>
<p>This is where you choose the car transmission in the drop-down menu.</p></td>
<td>TRAN-</td>
<td><p>TRAN-A</p>
<p>(default value)</p></td>
</tr>
<tr class="even">
<td><p>Pickup Phone</p>
<p>Here you can enter the pickup office phone number.</p></td>
<td>PUPH-</td>
<td><p>PUPH-1233333333</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Drop Off Phone</p>
<p>Here you can enter the drop off office phone number.</p></td>
<td>DOPH-</td>
<td><p>DOPH-415747777</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Additional Equipment</p>
<p>This is where you can add any car feature/equipment required. It is free text.</p></td>
<td>EQP-</td>
<td><p>EQP-SAT NAV</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Air Conditioning</p>
<p>Select from the drop-down as preferred.</p></td>
<td>AC-</td>
<td><p>AC-TRUE</p>
<p>(default is FALSE)</p></td>
</tr>
<tr class="even">
<td><p>Airport Pickup</p>
<p>This is a drop-down menu where you select if the pickup will be at the airport or not.</p></td>
<td>PU-</td>
<td><p>PU-FALSE</p>
<p>(default value)</p></td>
</tr>
<tr class="odd">
<td><p>Airport Drop Off</p>
<p>This is a drop-down menu where you select if the drop off will be at the airport or not.</p></td>
<td>DO-</td>
<td><p>DO-TRUE</p>
<p>(default is FALSE)</p></td>
</tr>
</tbody>
</table>

# HOTEL TAB

This is where all the details regarding the proposal for a Hotel segment
are added.

## Hotel Tab completion flow

## Hotel Tab screenshot example

<img src="./media/image8.png" style="width:6.67164in;height:2.64976in" />

##  Hotel Tab table of definitions 

### Hotel Tab mandatory information

<table>
<colgroup>
<col style="width: 49%" />
<col style="width: 23%" />
<col style="width: 26%" />
</colgroup>
<thead>
<tr class="header">
<th><p>File input</p>
<p>and description</p></th>
<th>PNR Remark label</th>
<th>PNR Remark examples</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>HOTEL</p>
<p>This is the tab name and the segment type.</p></td>
<td>SEG-</td>
<td>SEG-HOT</td>
</tr>
<tr class="even">
<td><p>(1) Country Code</p>
<p>This is the destination two-letter country code.</p></td>
<td>CO-</td>
<td>CO-GB</td>
</tr>
<tr class="odd">
<td><p>(2) Destination City</p>
<p>This is the destination city name in full</p></td>
<td>CITY-</td>
<td>CITY-LONDON</td>
</tr>
<tr class="even">
<td><p>(3) Hotel Name</p>
<p>This is where you enter the hotel name.</p></td>
<td>HTLNAME-</td>
<td>HTLNAME-LEA PALACE</td>
</tr>
<tr class="odd">
<td><p>(4) Check-In Date and Time</p>
<p>This is the check-in date and time using the following format:</p>
<ul>
<li><p>Date is in the format DD/MMM/YYYY</p></li>
<li><p>Time is in the format HHMM and is 24 hours</p></li>
</ul></td>
<td>DTE-…/AT-</td>
<td>DTE-2021-06-28/AT-1520</td>
</tr>
<tr class="even">
<td><p>(5) Check-Out Date and Time</p>
<p>This is the check-out date and time using the following format:</p>
<ul>
<li><p>Date is in the format DD/MMM/YYYY</p></li>
<li><p>Time is in the format HHMM and is 24 hours</p></li>
</ul></td>
<td>DTE-…/AT-</td>
<td>DTE-2021-06-30/AT-1200</td>
</tr>
<tr class="odd">
<td><p>(6) Confirmation Number</p>
<p>This is where you will add the provider reference if you have selected “Booked”.</p>
<p>This is only mandatory when Booked is checked.</p></td>
<td>CONF-</td>
<td><p>CONF-ABCDEF</p>
<p>CONF-NA</p>
<p>(default value if blank)</p></td>
</tr>
<tr class="even">
<td><p>(7) Supplier Name</p>
<p>This is where you enter the supplier name in full.</p></td>
<td>SUP-</td>
<td>SUP-SHERATON</td>
</tr>
<tr class="odd">
<td><p>(8) Currency</p>
<p>This is the three-letter ISO standard code for the currency used (eg GBP, EUR).</p></td>
<td>CURR-</td>
<td>CURR-GBP</td>
</tr>
<tr class="even">
<td><p>(9) Rate</p>
<p>This is the total amount of the Hotel segment.</p>
<p>It will automatically format to 2 decimal places if not typed.</p>
<p>We currently only support decimalized currencies.</p></td>
<td>VAL-</td>
<td>VAL-125.20</td>
</tr>
</tbody>
</table>

## Hotel Tab optional information

<table>
<colgroup>
<col style="width: 45%" />
<col style="width: 16%" />
<col style="width: 38%" />
</colgroup>
<thead>
<tr class="header">
<th><p>File input</p>
<p>and description</p></th>
<th>PNR Remark label</th>
<th><p>PNR Remark examples</p>
<p>with default value information</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Destination IATA</p>
<p>This is the IATA three-letter code of the destination city.</p></td>
<td>IATA-</td>
<td><p>IATA-LYS</p>
<p>(shows as IATA-/ if blank)</p></td>
</tr>
<tr class="even">
<td><p>Booked</p>
<p>If you check “Booked”, the “Confirmation Number” field will become mandatory.</p></td>
<td>BKD-</td>
<td><p>BKD-FALSE</p>
<p>(default value)</p></td>
</tr>
<tr class="odd">
<td><p>Confirmation Number</p>
<p>This is where you add the provider confirmation number if the hotel has been booked directly with the provider.</p>
<p>This is optional when “Booked” is not selected.</p></td>
<td>CONF-</td>
<td><p>CONF-A123456</p>
<p>or</p>
<p>CONF-NA</p>
<p>(default value)</p></td>
</tr>
<tr class="even">
<td><p>Location Details</p>
<p>This is a free text field where you can add information about the hotel location.</p></td>
<td>NOTE-</td>
<td><p>NOTE-DOWNTOWN</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Hotel Address</p>
<p>This is where you add the hotel address information.</p></td>
<td>ADD-</td>
<td><p>ADD-ASTON ROAD, LONDON</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Hotel Zip Code</p>
<p>This is the zip code of the hotel location</p></td>
<td>ZIP-</td>
<td><p>ZIP-LW45 6ER</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Phone Number</p>
<p>This is where you add the hotel phone number</p></td>
<td>PH-</td>
<td><p>PH-0044 1256321</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Policy Compliance Level (%)</p>
<p>This will be a value between 0-100 that matches the segment compliance (100 if fully compliant and 0 if not compliant at all).</p></td>
<td>LVL-</td>
<td><p>LVL-100</p>
<p>(shows as LVL-/ if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Room Type</p>
<p>This is where you can enter the room type in full.</p>
<p>It is free text.</p></td>
<td>ROOM-</td>
<td><p>ROOM-DOUBLE</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Comments</p>
<p>This is where you can add any additional comments such as cancellation policy.</p></td>
<td>RMKS-</td>
<td><p>RMKS-24HR CXX POLICY</p>
<p>(not shown if blank)</p></td>
</tr>
</tbody>
</table>

## RAIL TAB

This is where all the details regarding the rail segment are added.

## Rail Tab completion flow for one-way rail

## Rail Tab one-way screenshot example

<img src="./media/image9.png" style="width:6.69375in;height:2.76157in" />

## Rail Tab one-way table of definitions

### Rail Tab one-way mandatory information

<table>
<colgroup>
<col style="width: 55%" />
<col style="width: 15%" />
<col style="width: 29%" />
</colgroup>
<thead>
<tr class="header">
<th><p>File input</p>
<p>and description</p></th>
<th>PNR Remark label</th>
<th>PNR Remark examples</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RAIL – One Way</p>
<p>This is the tab name and the segment type.</p></td>
<td>SEG-</td>
<td>SEG-RAIL1</td>
</tr>
<tr class="even">
<td><p>Booked</p>
<p>Check the field “Booked” if you have confirmed the booking with the provider. The “Confirmation Number” field will then become mandatory.</p></td>
<td>BKD-</td>
<td><p>BKD-FALSE</p>
<p>(default value)</p></td>
</tr>
<tr class="odd">
<td><p>(1) Currency</p>
<p>This is the three-letter ISO standard code for the currency used (eg GBP, EUR).</p></td>
<td>CURR-</td>
<td>CURR-EUR</td>
</tr>
<tr class="even">
<td><p>(2) Fare</p>
<p>This is the total amount of the rail segment.</p>
<p>It will automatically format to 2 decimal places if not typed.</p>
<p>We currently only support decimalized currencies.</p></td>
<td>VAL-</td>
<td>VAL-250.00</td>
</tr>
<tr class="odd">
<td><p>(3) Booking Source</p>
<p>This is the rail provider booking source. It is a drop-down menu of the supported providers.</p></td>
<td>TYPE-</td>
<td>TYPE-2C</td>
</tr>
<tr class="even">
<td><p>(4) Departure Country Code</p>
<p>This is the two-letter IATA departure country code.</p></td>
<td>CO-</td>
<td>CO-FR</td>
</tr>
<tr class="odd">
<td><p>(5) Departure Station Name</p>
<p>This is the departure station name from the drop down provided and includes the departure rail station code. Items in the list are supplier specific.</p></td>
<td><p>CODE-</p>
<p>NAME-</p></td>
<td><p>CODE-FRDHP</p>
<p>NAME-PARIS MONTPARNASSE 2 PASTEUR</p></td>
</tr>
<tr class="even">
<td><p>(6) Confirmation Number</p>
<p>This is where you will add the provider reference if you have selected “Booked”. This is only mandatory when Booked is checked.</p></td>
<td>CONF-</td>
<td><p>CONF-A123456</p>
<p>or</p>
<p>CONF-NA</p>
<p>(default value)</p></td>
</tr>
<tr class="odd">
<td><p>(7) Arrival Country Code</p>
<p>This is the two-letter IATA arrival country code.</p>
<p>It is a drop-down menu.</p></td>
<td>CO-</td>
<td>CO-GB</td>
</tr>
<tr class="even">
<td><p>(8) Arrival Station Name</p>
<p>This is the arrival station name from the drop down provided and includes the rail station code. Items in the list are supplier specific.</p></td>
<td><p>CODE-</p>
<p>NAME-</p></td>
<td><p>CODE-GBBLL</p>
<p>NAME-BLACKFRIARS LONDON</p></td>
</tr>
<tr class="odd">
<td><p>(9) Carrier Name</p>
<p>This is the carrier name in full.</p></td>
<td>SUP-</td>
<td>SUP-EUROSTAR</td>
</tr>
<tr class="even">
<td><p>(10) Departure Date and Time</p>
<p>This is the departure date and time using the following format:</p>
<ul>
<li><p>Date is in the format DD/MMM/YYYY</p></li>
<li><p>Time is in the format HHMM and is 24 hours</p></li>
</ul></td>
<td>DTE-…/AT-</td>
<td>DTE-2021-06-29/AT-0850</td>
</tr>
<tr class="odd">
<td><p>(11) Arrival Date and Time</p>
<p>This is the arrival date and time using the following format:</p>
<ul>
<li><p>Date is in the format DD/MMM/YYYY</p></li>
<li><p>Time is in the format HHMM and is 24 hours</p></li>
</ul></td>
<td>DTE-…/AT-</td>
<td>DTE-2021-07-29/AT-1100</td>
</tr>
</tbody>
</table>

### Rail Tab one-way optional information

<table>
<colgroup>
<col style="width: 55%" />
<col style="width: 15%" />
<col style="width: 29%" />
</colgroup>
<thead>
<tr class="header">
<th><p>File input</p>
<p>and description</p></th>
<th>PNR Remark label</th>
<th><p>PNR Remark examples</p>
<p>with default value information</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Booked</p>
<p>Check the field “Booked” if you have confirmed the booking with the provider. “Confirmation Number” field will then become mandatory</p></td>
<td>BKD-</td>
<td><p>BKD-FALSE</p>
<p>(default value)</p></td>
</tr>
<tr class="even">
<td><p>Confirmation Number</p>
<p>This is where you add the provider confirmation number if applicable. This is optional if “Booked” is not checked.</p></td>
<td>CONF-</td>
<td><p>CONF-A12345</p>
<p>or</p>
<p>CONF-NA</p>
<p>(default value)</p></td>
</tr>
<tr class="odd">
<td><p>Class of Services</p>
<p>This is the class of services in full.</p></td>
<td>C-</td>
<td><p>C-STANDARD</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Duration</p>
<p>This is the trip duration in minutes.</p></td>
<td>DUR-</td>
<td><p>DUR-280</p>
<p>(shows as DUR-/ if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Train Number</p>
<p>This is where you add the train number.</p></td>
<td>TRN-</td>
<td><p>TRN-4</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Wagon Number</p>
<p>This is where you add the wagon number.</p></td>
<td>WAG-</td>
<td><p>WAG-8</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Seat Number</p>
<p>This is where you add the seat number.</p></td>
<td>SEAT-</td>
<td><p>SEAT-1C</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Policy Compliance Level (%)</p>
<p>This will be a value between 0-100 that matches the segment compliance (100 if fully compliant and 0 if not compliant at all).</p></td>
<td>LVL-</td>
<td><p>LVL-70</p>
<p>(shows as LVL-/ if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Comments</p>
<p>This is where you add any free text information.</p></td>
<td>RMKS-</td>
<td><p>RMKS-QUIET ZONE AVAILABLE</p>
<p>(not shown if blank)</p></td>
</tr>
</tbody>
</table>

## Rail Tab completion flow for round trip rail

***  
***

## Rail Tab round trip screenshot examples

### Rail Tab round trip input display

<img src="./media/image10.png" style="width:6.6791in;height:2.18986in" />

### Rail Tab round trip output display

<img src="./media/image11.png" style="width:6.69375in;height:2.89653in" />

## Rail Tab round trip table of definitions

### Rail Tab round trip mandatory information

<table>
<colgroup>
<col style="width: 47%" />
<col style="width: 21%" />
<col style="width: 30%" />
</colgroup>
<thead>
<tr class="header">
<th><p>File input</p>
<p>and description</p></th>
<th>PNR Remark label</th>
<th>PNR Remark examples</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RAIL – Round Trip</p>
<p>This is the tab name and the segment type.</p></td>
<td>SEG-</td>
<td><p>SEG-RAIL1</p>
<p>SEG-RAIL2</p></td>
</tr>
<tr class="even">
<td><p>(1) Currency</p>
<p>This is the three-letter ISO standard code for the currency used (eg GBP, EUR).</p></td>
<td>CURR-</td>
<td>CURR-EUR</td>
</tr>
<tr class="odd">
<td><p>(2) Fare</p>
<p>This is the total amount of the rail segment.</p>
<p>Automatically formatted to 2 decimal places if not typed.</p>
<p>We currently only support decimalized currencies.</p></td>
<td>VAL-</td>
<td>VAL-250.00</td>
</tr>
<tr class="even">
<td><p>(3) Booking Source</p>
<p>This is the rail provider booking source. It is a drop-down menu of currently supported rail providers.</p></td>
<td>TYPE-</td>
<td>TYPE-2C</td>
</tr>
<tr class="odd">
<td><p>(4) Departure Country Code</p>
<p>This is the two-letter IATA departure country code.</p></td>
<td>CO-</td>
<td>CO-FR</td>
</tr>
<tr class="even">
<td><p>(5) Departure Station Name</p>
<p>This is the departure station name from the drop down provided and includes the departure rail station code.</p>
<p>Items in the list are supplier specific.</p></td>
<td><p>CODE-</p>
<p>NAME-</p></td>
<td><p>CODE-FRDHP</p>
<p>NAME-PARIS MONTPARNASSE 2 PASTEUR</p></td>
</tr>
<tr class="odd">
<td><p>(6) Confirmation Number</p>
<p>This is where you will add the provider reference if you have selected “Booked”.</p>
<p>This is only mandatory when “Booked” is checked.</p></td>
<td>CONF-</td>
<td><p>CONF-A123456</p>
<p>or</p>
<p>CONF-NA</p>
<p>(default value)</p></td>
</tr>
<tr class="even">
<td><p>(7) Arrival Country Code</p>
<p>This is the two-letter IATA arrival country code.</p>
<p>It is a drop-down menu.</p></td>
<td>CO-</td>
<td>CO-GB</td>
</tr>
<tr class="odd">
<td><p>(8) Arrival Station Name</p>
<p>This is the arrival station name from the drop down provided in the file and includes the rail station code.</p>
<p>Items in the list are supplier specific.</p></td>
<td><p>CODE-</p>
<p>NAME-</p></td>
<td><p>CODE-GBBLL</p>
<p>NAME-BLACKFRIARS LONDON</p></td>
</tr>
<tr class="even">
<td><p>(9) Carrier Name</p>
<p>This is the carrier name in full.</p></td>
<td>SUP-</td>
<td>SUP-EUROSTAR</td>
</tr>
<tr class="odd">
<td><p>(10) Departure Date and Time</p>
<p>This is the departure date and time using the following format:</p>
<ul>
<li><p>Date is in the format DD/MMM/YYYY</p></li>
<li><p>Time is in the format HHMM and is 24 hours</p></li>
</ul></td>
<td>DTE-…/AT-</td>
<td>DTE-2021-06-29/AT-0850</td>
</tr>
<tr class="even">
<td><p>(11) Arrival Date and Time</p>
<p>This is the arrival date and time using the following format:</p>
<p>• Date is in the format DD/MMM/YYYY</p>
<p>• Time is in the format HHMM and is 24 hours</p></td>
<td>DTE-…/AT-</td>
<td>DTE-2021-07-29/AT-1100</td>
</tr>
<tr class="odd">
<td><p>(12) Return Departure Date</p>
<p>This is the return departure date and time using the following format:</p>
<p>• Date is in the format DD/MMM/YYYY</p>
<p>• Time is in the format HHMM and is 24 hours</p></td>
<td>DTE-…/AT-</td>
<td>DTE-2021-07-02/AT-0820</td>
</tr>
<tr class="even">
<td><p>(13) Return Arrival Date</p>
<p>This is the return arrival date and time using the following format:</p>
<p>• Date is in the format DD/MMM/YYYY</p>
<p>• Time is in the format HHMM and is 24 hours</p></td>
<td>DTE-…/AT-</td>
<td>DTE-2021-07-02/AT-1000</td>
</tr>
<tr class="odd">
<td><p>(14) Return Carrier Name</p>
<p>This is the return carrier name in full.</p></td>
<td>SUP-</td>
<td>SUP-THALYS</td>
</tr>
</tbody>
</table>

*  
*

### Rail Tab round trip optional information

<table>
<colgroup>
<col style="width: 43%" />
<col style="width: 20%" />
<col style="width: 36%" />
</colgroup>
<thead>
<tr class="header">
<th><p>File input</p>
<p>and description</p></th>
<th>PNR Remark label</th>
<th><p>PNR Remark examples</p>
<p>with default values</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Booked</p>
<p>Check the field “Booked” if you have confirmed the booking with the provider. The “Confirmation Number” field will then become mandatory.</p></td>
<td>BKD-</td>
<td><p>BKD-FALSE</p>
<p>(default value)</p></td>
</tr>
<tr class="even">
<td><p>Confirmation Number</p>
<p>This is where you add the provider confirmation number if applicable.</p>
<p>This is optional when “Booked” is not selected.</p></td>
<td>CONF-</td>
<td><p>CONF-B12345</p>
<p>or</p>
<p>CONF-NA</p>
<p>(default value)</p></td>
</tr>
<tr class="odd">
<td><p>Class of Services</p>
<p>This is the class of services in full, not just the letter.</p></td>
<td>C-</td>
<td><p>C-STANDARD</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Duration</p>
<p>This is the trip duration in minutes.</p></td>
<td>DUR-</td>
<td><p>DUR-280</p>
<p>(shows as DUR-/ if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Train Number</p>
<p>This is where you add the train number.</p></td>
<td>TRN-</td>
<td><p>TRN-4</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Wagon Number</p>
<p>This is where you add the wagon number.</p></td>
<td>WAG-</td>
<td><p>WAG-8</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Seat Number</p>
<p>This is where you add the seat number.</p></td>
<td>SEAT-</td>
<td><p>SEAT-1C</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Policy Compliance Level (%)</p>
<p>This will be a value between 0-100 that matches the segment compliance (100 if fully compliant and 0 if not compliant at all).</p></td>
<td>LVL-</td>
<td><p>LVL-70</p>
<p>(shows as LVL-/ if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Comments</p>
<p>This is where you add any free text information.</p></td>
<td>RMKS-</td>
<td><p>RMKS-QUIET ZONE AVAILABLE</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Return Confirmation Number</p>
<p>This is where you add the provider confirmation number if the rail travel has been booked directly with the provider.</p>
<p>This is optional if “Booked” is not selected.</p></td>
<td>CONF-</td>
<td><p>CONF-NA</p>
<p>(default value)</p></td>
</tr>
<tr class="odd">
<td><p>Return Class of Services</p>
<p>This is the class of services in full, not just the letter.</p></td>
<td>C-</td>
<td><p>C-STANDARD</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Return Duration</p>
<p>This is the return trip duration in minutes.</p></td>
<td>DUR-</td>
<td><p>DUR-60</p>
<p>(shows as DUR-/ if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Return Train Number</p>
<p>This is where you add the train number.</p></td>
<td>TRN-</td>
<td><p>TRN-Z202</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Return Wagon Number</p>
<p>This is where you add the wagon number.</p></td>
<td>WAG-</td>
<td><p>WAG-G2</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Return Seat Number</p>
<p>This is where you add the seat number.</p></td>
<td>SEAT-</td>
<td><p>SEAT-24A</p>
<p>(not shown if blank)</p></td>
</tr>
<tr class="even">
<td><p>Return Policy Compliance Level (%)</p>
<p>This will be a value between 0-100 that matches the segment compliance (100 if fully compliant and 0 if not compliant at all).</p></td>
<td>LVL-</td>
<td><p>LVL-100</p>
<p>(shows as LVL-/ if blank)</p></td>
</tr>
<tr class="odd">
<td><p>Return Comments</p>
<p>This is where you add any free text information.</p></td>
<td>RMKS-</td>
<td><p>RMKS-HERE ARE THE COMMENTS RELATED TO THE RETURN TRAVEL</p>
<p>(not shown if blank)</p></td>
</tr>
</tbody>
</table>

## CONCATENATION

Remark concatenation allows for multiple remark lines to be copied in a
single block. Where the maximum number of concatenations has been
reached, a new remark block will be created. This ensures that the
minimum number of copy and paste actions is required.

For more information on configuring concatenation, please see
[Configuration](#configuration) above.

<u>Example of blocks:</u>

@:5P/APTR/33/PROP1/SEG-RAIL1/BKD-FALSE+@:5P/APTR/57/PROP1/SEG-RAIL1/RMKS-NO
OTHER PLACES AVAILABLE //+@:5P/APTR/30/PROP1/SEG-RAIL1/IN
ECO+@:5P/APTR/31/PROP1/SEG-RAIL1/CONF-NA+@:5P/APTR/46/PROP1/SEG-RAIL1/DTE-2021-06-29/AT-0650+@:5P/APTR/46/PROP1/SEG-RAIL1/DTE-2021-06-29/AT-1100+@:5P/APTR/41/PROP1/SEG-RAIL1/PNR-2NCMIA/LVL-70+@:5P/APTR/36/PROP1/SEG-RAIL1/SUP-EUROSTAR+@:5P/APTR/50/PROP1/SEG-RAIL1/S/CO-FR/CODE-FRDHP/TYPE-2C

@:5P/APTR/57/PROP1/SEG-RAIL1/NAME-PARIS MONTPARNASSE 2
PASTEUR+@:5P/APTR/50/PROP1/SEG-RAIL1/E/CO-GB/CODE-GBBLL/TYPE-2C+@:5P/APTR/47/PROP1/SEG-RAIL1/NAME-BLACKFRIARS
LONDON+@:5P/APTR/38/PROP1/SEG-RAIL1/CURR-EUR/VAL-0+@:5P/APTR/39/PROP1/SEG-RAIL1/C-FIRST/DUR-280+@:5P/APTR/35/PROP1/SEG-RAIL1/TRN-4/WAG-8+@:5P/APTR/31/PROP1/SEG-RAIL1/SEAT-1C+@:5P/APTR/33/PROP1/SEG-RAIL2/BKD-FALSE+@:5P/APTR/53/PROP1/SEG-RAIL2/RMKS-HERE
ARE THE COMMENTS //

@:5P/APTR/50/PROP1/SEG-RAIL2/RELATED TO THE INBOUND
LEG+@:5P/APTR/31/PROP1/SEG-RAIL2/CONF-NA+@:5P/APTR/46/PROP1/SEG-RAIL2/DTE-2021-07-02/AT-0820+@:5P/APTR/46/PROP1/SEG-RAIL2/DTE-2021-07-02/AT-1000+@:5P/APTR/40/PROP1/SEG-RAIL2/PNR-2NCMIA/LVL-/+@:5P/APTR/34/PROP1/SEG-RAIL2/SUP-THALYS+@:5P/APTR/50/PROP1/SEG-RAIL2/S/CO-GB/CODE-GBBLL/TYPE-2C+@:5P/APTR/47/PROP1/SEG-RAIL2/NAME-BLACKFRIARS
LONDON+@:5P/APTR/50/PROP1/SEG-RAIL2/E/CO-FR/CODE-FRDHP/TYPE-2C

@:5P/APTR/57/PROP1/SEG-RAIL2/NAME-PARIS MONTPARNASSE 2
PASTEUR+@:5P/APTR/43/PROP1/SEG-RAIL2/CURR-EUR/VAL-250.00+@:5P/APTR/29/PROP1/SEG-RAIL2/DUR-/+@:5P/APTR/35/PROP1/SEG-RAIL2/TRN-6/WAG-8

# REMARK SEPARATORS

Remark entries use a single forward slash between fields but may also
contain a double forward slash for long remark content.

The single forward slash **/** denotes the end of a field and the
beginning of the next field.

A forward slash **/** is a **reserved character** and should **not** be
added in any field.

The double forward slash **//** denotes that the content is longer than
the line length permitted by the GDS. The remaining content is then
split into a new entry or entries with no label. The number of splits
will depend on how many are required.

Double slash example:

@:5P/APTR/54/PROP1/SEG-AIR2/RMKS-**COMMENTS FOR THE RETURN**

//+@:5P/APTR/34/PROP1/SEG-AIR2/**AIR SEGMENT**

# VERSION HISTORY

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 66%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Data Formatter for Concur Request Version Number</strong></th>
<th>Amendments dates</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>V2.10</p>
<p>v2.11</p>
<p>v2.12</p>
<p>v2.12.1</p></td>
<td><p><strong>02Jun21</strong></p>
<p>ALL TABS :</p>
<ul>
<li><p>Time - can now be entered manually only</p></li>
<li><p>Date - user can manually enter the date or use the calendar</p>
<p>AIR, CAR, HOTEL and RAIL TABS:</p></li>
<li><p>Fare/Rate - two decimals will be added automatically if not entered in the corresponding field</p></li>
<li><p>Policy compliance - accept only numeric value between 0 and 100</p>
<p>AIR and RAIL TABS:</p></li>
<li><p>Policy compliance - will now show for each leg in case of return trips</p>
<p>AIR TAB:</p></li>
<li><p>Departure/Arrival Details - Mandatory and Optional information are now on the same block for the air one-way segment</p></li>
<li><p>Return Details - Mandatory and optional information are now on the same block</p>
<p>RAIL TAB:</p></li>
<li><p>Departure/Arrival Details - Mandatory and optional information are now on the same block for the rail one-way segment</p></li>
<li><p>Return Details - Mandatory and optional information are now on the same block</p>
<p>CAR TAB:</p></li>
<li><p>Drop Off Details - this field is now optional</p>
<p>OPTIONAL INFORMATION</p></li>
<li><p>We will show the data in the remarks only if the value is entered in the file.(please refer to each optional field for each segment</p>
<p><strong>07Jun21</strong></p>
<p>CAR TAB</p></li>
<li><p>Location data has now been added</p></li>
<li><p>Drop Off Details is now optional</p></li>
</ul>
<p>ALL TABS</p>
<ul>
<li><p>Currency fields will now accept only alpha characters</p></li>
</ul>
<p>AIR and RAIL TAB</p>
<ul>
<li><p>For return trips we have now all the information boxes on the same page</p>
<p>GENERATE CODE</p></li>
<li><p>Introduction of the concatenation of the remarks</p>
<p><strong>28Jun21</strong></p></li>
<li><p>Concatenation has been implemented</p></li>
<li><p>Bug fixes (Hotel Phone now populated in the remarks when added, double “/” in the car remarks)</p>
<p><strong>30Jun21</strong></p></li>
<li><p>File name has been updated</p></li>
<li><p>UI updates (adding “Return” before “Confirmation number” and “Policy Compliance Level” fields)</p></li>
</ul></td>
</tr>
</tbody>
</table>

N.B. This document v1.2 is a guide for the file v2.12 and supersedes any
previous documentation
