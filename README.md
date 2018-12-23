# twitter_bot
How to use twitter through comand line?


import tweepy  #python library to deal with twitter
import argparse #this way I can do everything through the command line.

parser = argparse.ArgumentParser(description = 'My Twitter bot')
parser.add_argument('-t', action = 'store', dest = 't')
parser.add_argument('-rt', action = 'store', dest = 'rt')
parser.add_argument('--tl', action="store_true", default=False)

consumer_key = 'xxxx  '
consumer_secret = 'xxxx'

access_token = 'xxxx'
access_token_secret = 'xxxx'

auth = tweepy.OAuthHandler(consumer_key, consumer_secret)
auth.set_access_token(access_token, access_token_secret)

api = tweepy.API(auth)

args = parser.parse_args()

if args.tl:
    for tweet in api.home_timeline():
        print(tweet.id)
        print(tweet.text)
        print('\n')
        
if args.t:
    api.update_status(args.t)
    print('Your tweet has been updated')

if args.rt:
    api.retweet(args.rt)
    print('Your tweet has been posted successfully')
