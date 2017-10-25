A stream of conciousness overview of the trading platform.

# Summary
The message bus, Kafka, will be used as a separation of concerns for all pieces of the architecture.
Identifiable pieces are:

* Singal Services
 - Microservices which subsribe to market data topics request entry and exist.
* Risk Manager
 - Ensures that any defined risk for a portfolio is adhered
* Order Manager
 - When an order is placed this service will try to fill the order.
 - Depending on how this is architected we can have an proxy service that dispatches
   order requests to different microservices or me a monolith with several strategies
   included. 
* Data injest
 - These microservices will take data from various input providers and transform them into a
   common market data format.

# Market Data
Markets are brokent into several depth.  Last trade, bid ask, spread, and the depth of the order book.
We may want to integrate FIX data but a simple market data input will be started off with first.

Several strategies should be able to subscribe to the same symbol.

# Replay vs Live
Strategies should not care if a system is live or being backtested. The same code should be used.  
