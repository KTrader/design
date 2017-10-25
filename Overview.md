A stream of conciousness overview of the trading platform.

# Summary
The message bus, Kafka, will be used as a separation of concerns for all pieces of the architecture.
Identifiable pieces are:

* Signal Services
 - Subscribe to market data topics request entry and exist.
* Risk Manager
 - Ensures that any defined risk for a portfolio is adhered
* Order Manager
 - When an order is placed this service will try to fill the order.
 - We can have an proxy service that dispatches order requests to different micro-services 
   or a monolith with several execution strategies included. 
* Data ingest
 - Consume and transform marked data from various sources and publish them to topics in a common market data format.

# Market Data
Markets are broken into several depth.  Last trade, bid ask, spread, and the depth of the order book.
We may want to integrate FIX data but a simple market data input will be started off with first.

Several strategies should be able to subscribe to the same symbol.

# Replay vs Live
Strategies should not care if a system is live or a back-test. The same code should be used.  
