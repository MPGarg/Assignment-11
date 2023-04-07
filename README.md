# Assignment-11

## Problem Statement

![image](https://user-images.githubusercontent.com/120099863/230622045-c3056f96-ead2-4f9e-95e4-54506c5cf477.png)

## Part 1: BERT

* Data related to Space Exploration was collected and stored in training.txt file. 

* Sample lines from dataset:
"Why is Mars called the Red Planet?
The bright rust color Mars is known for is due to iron-rich minerals in its regolith — the loose dust and rock covering its surface. Earth's soil is a kind of regolith, too, albeit one loaded with organic content. According to NASA, the iron minerals oxidize, or rust, causing the soil to look red."

Training Log of last few steps:
it: 1700  | loss 4.35  | Δw: 2.386
it: 1720  | loss 4.34  | Δw: 2.343
it: 1740  | loss 4.28  | Δw: 2.199
it: 1760  | loss 4.21  | Δw: 2.131
it: 1780  | loss 4.3  | Δw: 2.376
it: 1800  | loss 4.32  | Δw: 2.243
it: 1820  | loss 4.22  | Δw: 2.182
it: 1840  | loss 4.27  | Δw: 2.508
it: 1860  | loss 4.3  | Δw: 2.338
it: 1880  | loss 4.24  | Δw: 2.304
it: 1900  | loss 4.24  | Δw: 2.402
it: 1920  | loss 4.2  | Δw: 2.394
it: 1940  | loss 4.2  | Δw: 2.607
it: 1960  | loss 4.23  | Δw: 2.604
it: 1980  | loss 4.27  | Δw: 2.513

Code lines to apply random noise:
#apply random word 
        s1 = []
        for w in s:
          if random.random() < p_random_mask:
              prob = random.random()
              if prob < 0.8:
                  st = [dataset.MASK_IDX, w]
                  s1.append(st)                  
              elif prob < 0.9:
                  #any random word 10% of 15%
                  st = [dataset.vocab[dataset.rvocab[random.randrange(dataset.vocab_size)]], w]
                  s1.append(st)
              else:
                  #same word 10% of 15%
                  st = [w,w]
                  s1.append(st)
          else:
              st = [w, dataset.IGNORE_IDX]
              s1.append(st)
                            
Testing Input Lines:
'<mask> is the fourth planet from the sun and has a distinct',
'The bright rust color <mask> is known for is due to iron-rich',
'Mars also has the <mask> volcanoes in the solar system, Olympus Mons',
'When Mars is closest to the <mask> its southern hemisphere is Cold',
'A graphic showing brief timeline of important <mask> missions and the top',
'<mask> storms are common on Mars. They can occur at any time',
'NASA has two other orbiters working around the <mask> — the Mars',
'The next two craft to successfully reach the Red <mask> were Mars',
'We now know that <mask> is very cold and dry, with no',
'Mars once had liquid <mask> on the surface and could have supported'
  
Output:
<oov> is the <oov> <oov> from the <oov> and <oov> a <oov>
the <oov> <oov> <oov> <oov> is <oov> for is <oov> to ,
<oov> also <oov> the <oov> , in the , , <oov> <oov>
<oov> <oov> is <oov> to the <oov> <oov> <oov> , is <oov>
a , <oov> <oov> , of <oov> <oov> <oov> and the <oov>
<oov> <oov> are <oov> on , they <oov> , at <oov> time
, <oov> <oov> <oov> , <oov> , the of , the <oov>
the <oov> <oov> <oov> to <oov> <oov> the <oov> of were <oov>
we <oov> <oov> that <oov> is <oov> <oov> and , with <oov>
<oov> <oov> had <oov> <oov> on the , and . have the
  
## Part 2: GPT
  
  
