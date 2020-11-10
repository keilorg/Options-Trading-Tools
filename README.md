# Options Pricing: Practice Tool

### Inspiration
  In my first year as an options trader at Susquehanna International Group, I created this tool to help me practice pricing equity options. As a trader, it was incredibly important that I be able to quickly and accurately price an options board (i.e. the calls & puts at various strike prices for a given expiration), determine at what price I would be willing to trade various market orders, and adjust my fair values given these market orders.

  This tool provides a practice options board with just enough initial information for the user to impute fair values for the entire board. Once the user has determined their fair values and made their markets, the tool has the ability to generate random market orders that the user can practice pricing. Finally, the tool has the ability to adjust the stock price of the board, allowing the user to practice thinking through how their fair values change given stock price fluctuations.



### Instructions for Use
  There are four sheets in the .xlsm document. The first sheet (Board) contains the practice tool, while the last three sheets (Fairs1, Fairs2, Orders) contain information on the backend that the macros in the first sheet use to populate the tool with fair values and synthetic market orders.
  
  The first sheet (see image below) is a simplified version of an equity options board with two months. Five strikes are included in each month, the call options are to be entered on the left side, and the puts on the right. The stock market is given at the top (per image, the best stock bid is 78.27 and the best offer is 78.29):

![Pic1](https://github.com/keilorg/Options-Trading-Tools/blob/main/Pic1.png)


  By pressing the “Random” macro in the top left corner, you can generate a random stock price with random volatility and interest rate within specified ranges. Using this generated stock, the model propagates the information cells to the right of each month’s section with information used to price the options at that specific strike. If no information is given, then it provides a market in one of the calls or puts. This information is all pulled from the second and third Fairs sheets. The information on the Fairs sheets was generated by put-option and call-option functions written using black-scholes options-pricing formula (see Module 2 in the VBA folder).
   
   I designed the macro such that the initial information provided in these cells will be enough to fully price the entire board (by making sure all flys are priceable with the given info). The user can practice using this initial information to price the whole board as quickly as possible. Once the user has a fair value in mind for each option, they should make a market around that fair value, a bid and an offer, which they can enter in the cells on either side of the cells with “-“ in them. An example of a completed board looks like this:

![Pic2](https://github.com/keilorg/Options-Trading-Tools/blob/main/Pic2.png)


There's a “Toggle Fairs” macro that allows the user to reveal the fair values of the options on the board once they finish making their markets. The “Toggle Fairs” macro is designed to replace the “-“ cells with the option's fair value, obtained from the Fairs sheets.

#### Resetting the Board
The user can reset the board using the “Reset” macro. It simply replaces any bids or offers the user entered with empty cells and replaces the option fair value cells with “-“ once again.

#### Adjusting Fair Values
The arrows in the middle of the page can be used to manipulate the underlying stock price. The left and right set of arrows are simply used to change the displayed bid and offer price of the stock. The middle set of arrows, however, changes the actual stock price used on the Fairs sheets, which correspondingly changes the fair value of all options on the board (thus, the fair values you see change when you toggle fairs).

The ten search-menu bars allow the user to select from a variety of different pieces of information applicable to the options involving that specific strike and expiration. This information is again all pulled from the Fairs sheets.

#### Market Order Simulation
The “New Order” macro, allows the user to simulate practice orders. The user can evaluate the risk of the order (mostly just delta and vega risk), and decide whether they want to trade the order at the given price. By highlighting the cells to the right of the new order cell, the user can see the fair price of the order, which is presented in white font. The orders are generated in Module 3 of the VBA folder, using information on the Orders sheet.
