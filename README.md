# Huffman-Coding
## Aim
To implement Huffman coding to compress the data using Python.

## Software Required
1. Anaconda - Python 3.7

## Algorithm:
### Step1:
Get the input String.

### Step2:
Create tree nodes.

### Step3:
Main function to implement huffman coding.

### Step4:
Calculate frequency of occurrence.

### Step5:
Print the characters and its huffmancode.

 
## Program:
```
Developed by : Vishranthi A
Reg no : 212221230124
```
``` Python
# Get the input String

string = '212221230124-Vishranthi A'


# Create tree nodes
class NodeTree(object):
    def __init__(self,left=None,right=None):
        self.left=left
        self.right=right
    def children (self):
        return (self.left,self.right)


# Main function to implement huffman coding
def huffman_code_tree(node,left=True,binString=''):
    if type(node) is str:
        return {node:binString}
    (l,r)=node.children()
    d=dict()
    d.update(huffman_code_tree(l, True, binString + '0'))
    d.update(huffman_code_tree(r, True, binString + '1'))
    return d


# Calculate frequency of occurrence

fre={}
for c in string:
    if c in fre:
        fre[c]+=1
    else:
        fre[c]=1
fre=sorted(fre.items() ,key=lambda x:x[1],reverse=True)
nodes=fre

while len(nodes)>1:
    (key1,c1)=nodes[-1]
    (key2,c2)=nodes[-2]
    nodes=nodes[:-2]
    node=NodeTree(key1,key2)
    nodes.append(node,c1+c2)
    
    nodes=sorted(nodes,key=lambda x:x[1],reverse=True)
  

# Print the characters and its huffmancode

huffmanCode=huffman_code_tree(nodes[0][0])

print(' Char | Huffman code ')
print('-----------------------')
for(char,frequency)in fre:
    print(" %-4r |%12s" % (char,huffmanCode[char]))

```
## Output:

### Print the characters and its huffmancode

![image](https://github.com/Vishranthi-arun/Huffman-Coding/assets/93427278/3752d98c-1f69-45fd-98b8-0e1ddd41e0ca)




## Result
Thus the huffman coding was implemented to compress the data using python programming.
