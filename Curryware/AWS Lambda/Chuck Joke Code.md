```
import json  
import boto3  
import random  
  
  
def get_chuck_jokes():  
    all_chuck_jokes = {  
        "dmppfaxjqnkfubpqzgcmxq": "Using his trademark roundhouse kick, Chuck Norris once made a fieldgoal in RJ Stadium in Tampa Bay from the 50 yard line of Qualcomm stadium in San Diego",  
        "sVASodJpQy-IvDlosBtPwA": "If you see Chuck Norris, and he's moving, it's already too late to run.",  
        "x0KE-UdnStSYuWbMDHtjaQ": "When Chuck Norris prepares a smoked salmon, he wraps it in Zig-Zag.",  
        "hzuvgphrtdmmbjdpnaxskw": "Chuck Norris breaks RSA 128-bit encrypted codes in milliseconds.",  
        "OXofDvjgTK2YOKlo4G8MXQ": "Legend has it that a weak, sickly 6 year boy named Chuck Norris was thrown into the River Styx by a gang of 10 year old bullies. The bullies were never seen or heard of again.",  
        "uAfX-jQDTyOapALDkxXSMQ": "The back of Chuck Norris' hands are always speckled with bone marrow.",  
        "Atzukpp6TqezwFBPm5SfsA": "The 3D Chuck Norris movie was rated RRRR because no one made it out of the theater. No one ever crosses Chuck Norris!",  
        "aHdJbcshSTyaL-RxS1Euhw": "Chuck Norris once had a staring contest with a picture of himself and won.",  
        "rNG1-KjWTwSqoyJqaOfBwQ": "Chuck Norris counts his chickens before he eats them.",  
        "Ujx2l4G3T-CYkpr_gKj9Jw": "What's the difference between Chuck Norris and Mud ? Mud comes off..",  
        "3hPN8nnHTIqw0PLHaFJtOQ": "Physicists have recently discovered that the universe began when Chuck Norris roundhouse-kicked a singularity (the big bang).",  
        "ezudm-intc6uvfuzreclpq": "If you spell Chuck Norris in Scrabble, you win. Forever.",  
        "BIYoIvIFTAuzsJ-sGfBtQg": "there is no use crying over spilled milk, unless its Chuck Norris' milk because then your gonna die",  
        "TVbuLkPVQ76HFRw3v2yJyA": "Chuck Norris wrote down that 1+1=4 on a math test and got it right.",  
        "0F0sF-qRQYyUqDVrBQm9IQ": "Chuck Norris doesn't look at the weather forecast. He DECIDES what the weather will be.",  
        "DGSMwgzPQcCKfY8mJsCYrg": "Chuck Norris can hit you so hard that not even Google will be able to find you.",  
        "3Oq0m_HDTiuZ13UPujVEfw": "Chuck Norris has never had to start back at 'square one'. If he ever messes up, he'll start back at octagon fifty-two.",  
        "IqZFykfiRu2UhKDMxN1BKg": "Trying to get the drop on Chuck Norris is like trying to put toothpaste back in the tube.",  
        "bQkaXL0yTu-ClefWChemwA": "Chuck Norris doesn't drink often. But when he does, he prefers to kick 'the most interesting man in the word' in the ass & take his Dos Equis.",  
        "D8o00FE0RNSNUlltwEPDVg": "Chuck Norris has a Grizzly Bear rug laid out on his family room floor. The Grizzly Bear isn't dead...it's just too afraid to move.",  
        "4pmKry_xQp6M1oEFfDuhAA": "Allstate may protect you from mayhem, but it is useless against Chuck Norris.",  
        "yM8nV5p5RmSgllUkZIgRfQ": "Superman has posters of Chuck Norris",  
        "PcDtUZBTRzmG6VqoF91Rlg": "The number pi isn't really infinite.Chuck Norris just hasn't told it to stop yet.",  
        "5xvm-ye0t9awb7xfgntxdq": "Contrary to popular belief, there is indeed enough Chuck Norris to go around.",  
        "JtZFGZbTRLOT-1Vww58wdQ": "There is a light at the end of every tunnel, just pray it's not the frieght train called Chuck Norris.",  
        "L22OR5llQJe3mZ4Iw6Nngw": "Chuck Norris was named valedictorian of his high school on the first day of his freshman year.",  
        "Zc9QJcwET_-SIRHlWOWMCQ": "Chuck Norris once ate an entire wildebeest with a broken KFC spork.",  
        "dCgJ2q_PQ_CredrAMbsgEg": "Chuck Norris has concealed weapons permits, so he can wear gloves.",  
        "DeRu2xJyR2aI1SgSHQtpEA": "the reason why babies cry when they are born is because they know they've been brought into the same world as Chuck Norris",  
        "K64oRq5dSv2_Op5q6cfGnw": "Facebook was originally Chuck Norris's personal webpage of pictures of the people he has roundhouse kicked in face.It filled up with so many people it leaked onto the internet.",  
        "jVdPAPXNThWxIpXU8uuQZA": "Chuck Norris' parents WERE the unstoppable force and the immovable object.",  
        "7Doq1q7vRgOwC-9-dQ0ZpA": "Chuck Norris gargles with thumbtacks.",  
        "HTdU5pF2TDqIj78XE9_KTA": "An elderly man accidentally let his Buick roll into Chuck Norris' new Lexus. Chuck was furious and got violent. Chuck punched out the Buick.",  
        "Zxcnvj5vRTWZmH_qmGY5hQ": "The speed of light is 186,000 miles per second. Chuck Norris' speed is unable to be calculated.",  
        "qd6wpqqyrhilhm1qnq24vq": "There is no theory of evolution, just a list of creatures Chuck Norris allows to live.",  
        "rc6-b6moRZywsVze1-xFXA": "Chuck Norris crab fishes the Bearing Sea using only a snorkel and a laundry basket.",  
        "F2KvzTFtQlOB7meyjE-Phg": "What is the difference between a diamond and Chuck Norris? Well one is the strongest substance on earth, the other is just compressed carbon.",  
        "FKjcTbgAT5eyxwooaWx6Uw": "Chuck Norris roundhouse kicked all the American out of Johnny Depp.",  
        "1KStppx0R4K7VwQkoGfKqg": "Chuck Norris once made a classical music station play the theme to Walker: Texas Ranger for 12 straight hours.",  
        "Uj74c4g4QMWWERfPj7FJAw": "Do not stare at Chuck Norris' beard, or it may feel threatened and leap off his face and smother you to death.",  
        "each6usssvavuwtvv3r95q": "The class object inherits from Chuck Norris",  
        "e3n-xmY0Qoir2Mv0AKPQxg": "The Kool-Aid Pitcherman busted through the wall of Chuck Norris' livingroom and said, OH NOOOOOOOO!.",  
        "BLzsX8RrS-iVGuJCXgNHtQ": "Chuck Norris thinks outside the box,then roundhouse kicks the box into oblivion.",  
        "MgNoaZdqTKCY35zJBwZJEg": "Freddy has nightmares about Chuck Norris",  
        "f9-bV3bBRwGLb-diMLDtlA": "The world was a cube. Until Chuck Norris got there!",  
        "Q3sxrdV2T_CqPphubDU4Ag": "It's a well-known fact that the most lethal substance on Earth is Chuck Norris adrenaline.",  
        "hpves7kxrm68d_rvcuuivg": "Chuck Norris does infinite loops in 4 seconds.",  
        "7F5dkgpkQMqnl30le_y3vw": "Chuck Norris skipped all grades simultaneously, including college. When he was two.",  
        "LpHcyuP_SPWcqadMXQduUQ": "Chuck Norris once roundhouse kicked a cotton field in Mississippi instantly creating the first Levis factory as well as adorning his torso with a sleeveless denim vest",  
        "0rLqrVMVTbuMkWF1urzQUQ": "Whoever said only the good die young was probably in Chuck Norris's kindergarten class."  
    }  
    return all_chuck_jokes  
  
  
def create_joke_json():  
    chuck_jokes = get_chuck_jokes()  
    total_jokes = len(chuck_jokes)  
    random_number = random.randint(0, total_jokes - 1)  
    joke_key = list(chuck_jokes)[random_number]  
    joke_text = chuck_jokes[joke_key]  
    joke_dictionary = {'joke_number': random_number, 'joke_id': joke_key, 'joke_text': joke_text}  
    json_string = json.dumps(joke_dictionary, indent=2)  
    return json_string  
  
  
# Press the green button in the gutter to run the script.  
if __name__ == '__main__':  
    print(create_joke_json())
```
