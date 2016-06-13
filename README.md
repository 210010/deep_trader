#Reinforcement-trading
This project uses Deep Q learning on stock market and agent tries to learn trading. The goal is to check if the agent can learn to read tape. The project is dedicated to hero in life great Jesse Livermore.


Process:
a) Intially I started by using chainer for the project for both supervised and reinforcement learning. In middle of it AlphaGo (https://research.googleblog.com/2016/01/alphago-mastering-ancient-game-of-go.html) came, so I shifted to read Sutton book (https://webdocs.cs.ualberta.ca/~sutton/book/the-book.html), AlphaGo paper and related paper, David Silver lectures (http://www0.cs.ucl.ac.uk/staff/d.silver/web/Teaching.html, they are great)
on Reinforcement learning. I am coming back to project after 45 days a lot has changed in TensorFlow all the cool kids (even Deepmind) have started using it. Hence, I am ditching chainer and will use tensorflow from now. Exciting times ahead.


#For the first iteration of the project
#Policy network:
I will be starting with simple feed-forward network. Though, I am also inclined to use convolutional network reason, they do very well when the minor change in input should not change ouput. For example: In image recognizition, a small pixel values change doesn't meam image is changed. Intutively stocks numbers look same to me, a small change should not trigger a trade but again the problem here comes with normalization. With normalization the big change in number will be reduced to a very small in inputs hence its good to start with feed-forward.

#feed-forward
I want to start with 2 layer first, yes that just vanilla but lets see how it works than will shift to more deeper network. On output side I will be using a sigmord non-linear function to get value out of 0 and 1. In hidden layer all neurons will be RELU. With 2 layers, I am assuming that first layer w1 can decide whether market is bullish, bearish and stable. 2nd layer can then decide what action to take based on based layer.

#training:
I will run x episode of training and each will have y time interval on it. Policy network will have to make x*y times decision of whether to hold, buy or short. After this based on our reward I will label every decison whether it was good/bad and update network. I will again run x episode on the improved network and will keep doing it. Like MCTS where things average out to optimality our policy also will start making more positive decision and less negative decision even though in training we will see policy wrong choices but on average it will work out because we will do same thing million times.

#Episodic 
I plan to start with episodic training rather than continous training. The major reason for this is that I will not have to calculate reward after every action which agent will make which is complex to do in trading, I can just make terminal reward based on portfolio value after an entire episode (inital value of portfolio - transaction cost occur inside the episode). The reason for doing it that I believe it will motivate agent to learn trading on episodic basic. It also means that I have to check the hypothesis on different episode of different length, also have to test thypothesis that what will happen if i give immediate reward after every time interval and also terminal reward based on what I discussed above. As usual like every AI projects, there will be a lot of hit and trial. 

I should better write good code and store all results properly so that I can compare them to see what works and what don't. Ofcourse the idea is to make sure agent remain profitable while trading. 




More info here:
https://docs.google.com/document/d/12TmodyT4vZBViEbWXkUIgRW_qmL1rTW00GxSMqYGNHU/edit


Data sources:
1) Nifty Data: https://drive.google.com/folderview?id=0B8e3dtbFwQWUZ1I5dklCMmE5M2M&ddrp=1%20%E2%81%A0%E2%81%A0%E2%81%A0%E2%81%A09:05%20PM%E2%81%A0%E2%81%A0%E2%81%A0%E2%81%A0%E2%81%A0


2) Nifty futures:http://www.4shared.com/folder/Fv9Jm0bS/NSE_Futures


3) Google finance: The package connects with Google Finance and downloads a spreadsheet from:http://www.google.com/finance/getprices?q=.DJI&x=INDEXDJX&i=60&p=10d&f=d,c,h,l,o,v with the date (intra-daily), closing price, high, low, open and volume.

You can adjust this to your own preferences by 'seeing' the code as:http://www.google.com/finance/getprices?q=TICKER&x=EXCHANGE&i=INTERVAL&p=PERIOD&f=d,c,h,l,o,v.

Where:

TICKER: is the unique ticker symbol

EXCHANGE: is where the security is listed on

Hint: to track these inputs, for instance for the Dow Jones Industrial Average, you search the security of interest at Google Finance and then you can find at the top: (INDEXDJX:.DJI) which obviously refers to (EXCHANGE:TICKER).
INTERVAL: defines the frequency (60 = 60 seconds)

PERIOD: is the historical data period (see also Google Finance), here 10d refers to the past 10 days (up to current time).


#Dependencies:
1) https://github.com/tensorflow/tensorflow
2) https://github.com/pfnet/chainer (if wants to use chainer)
3) https://github.com/blampe/IbPy

External help
1) https://github.com/nivwusquorum/tensorflow-deepq
2) Deep-Q-chainer
https://github.com/ugo-nama-kun/DQN-chainer


#for reading on getting data using IB
https://www.interactivebrokers.com/en/software/api/apiguide/tables/historical_data_limitations.htm

#Reinforcement learning resources
https://github.com/aikorea/awesome-rl , this is enough if you are serious



