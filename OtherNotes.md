## Day-2 (16/06/2021)
### Data Structure
#### Trie

```java
class TrieNode{
    
    public TrieNode[] children = null;
    public boolean isLeaf;
    
    public TrieNode(){
        children = new TrieNode[26];
    }
}

class Trie {
    
    private TrieNode root;
    
    /** Initialize your data structure here. */
    public Trie() {
        root = new TrieNode();
    }
    
    /** Inserts a word into the trie. */
    public void insert(String word) {
        TrieNode it = root;
        for(int i=0;i<word.length();i++){
            int idx = word.charAt(i)-'a';
            
            if(it.children[idx]==null){
                it.children[idx] = new TrieNode();
            }
            
            it = it.children[idx];
        }
        
        it.isLeaf = true;
    }
    
    /** Returns if the word is in the trie. */
    public boolean search(String word) {
        TrieNode node = searchHelper(word);
        return node!=null && node.isLeaf;
    }
    
    /** Returns if there is any word in the trie that starts with the given prefix. */
    public boolean startsWith(String prefix) {
        TrieNode node = searchHelper(prefix);
        return node!=null;
    }
    
    public TrieNode searchHelper(String word){
        TrieNode node = root;
        for(int i=0;i<word.length();i++){
            int idx = word.charAt(i) - 'a';
            if(node.children[idx]!=null){
                node = node.children[idx];
            }
            else{
                return null;
            }
        }
        
        return node;
    }
}

```

Resources
* [Problem Statement LeetCode](https://leetcode.com/problems/implement-trie-prefix-tree/)
* [Youtube video](https://youtu.be/99sP62PJZXc)
