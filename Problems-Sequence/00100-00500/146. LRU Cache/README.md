# [146. LRU Cache (Medium)](https://leetcode.com/problems/lru-cache/)

<p>Design a data structure that follows the constraints of a <strong><a href="https://en.wikipedia.org/wiki/Cache_replacement_policies#LRU" target="_blank">Least Recently Used (LRU) cache</a></strong>.</p>

<p>Implement the <code>LRUCache</code> class:</p>

<ul>
	<li><code>LRUCache(int capacity)</code> Initialize the LRU cache with <strong>positive</strong> size <code>capacity</code>.</li>
	<li><code>int get(int key)</code> Return the value of the <code>key</code> if the key exists, otherwise return <code>-1</code>.</li>
	<li><code>void put(int key, int value)</code>&nbsp;Update the value of the <code>key</code> if the <code>key</code> exists. Otherwise, add the <code>key-value</code> pair to the cache. If the number of keys exceeds the <code>capacity</code> from this operation, <strong>evict</strong> the least recently used key.</li>
</ul>

<p>The functions&nbsp;<code data-stringify-type="code">get</code>&nbsp;and&nbsp;<code data-stringify-type="code">put</code>&nbsp;must each run in <code>O(1)</code> average time complexity.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input</strong>
["LRUCache", "put", "put", "get", "put", "get", "put", "get", "get", "get"]
[[2], [1, 1], [2, 2], [1], [3, 3], [2], [4, 4], [1], [3], [4]]
<strong>Output</strong>
[null, null, null, 1, null, -1, null, -1, 3, 4]

<strong>Explanation</strong>
LRUCache lRUCache = new LRUCache(2);
lRUCache.put(1, 1); // cache is {1=1}
lRUCache.put(2, 2); // cache is {1=1, 2=2}
lRUCache.get(1);    // return 1
lRUCache.put(3, 3); // LRU key was 2, evicts key 2, cache is {1=1, 3=3}
lRUCache.get(2);    // returns -1 (not found)
lRUCache.put(4, 4); // LRU key was 1, evicts key 1, cache is {4=4, 3=3}
lRUCache.get(1);    // return -1 (not found)
lRUCache.get(3);    // return 3
lRUCache.get(4);    // return 4
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= capacity &lt;= 3000</code></li>
	<li><code>0 &lt;= key &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= value &lt;= 10<sup>5</sup></code></li>
	<li>At most 2<code>&nbsp;* 10<sup>5</sup></code>&nbsp;calls will be made to <code>get</code> and <code>put</code>.</li>
</ul>


**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Facebook](https://leetcode.com/company/facebook), [Apple](https://leetcode.com/company/apple), [Intuit](https://leetcode.com/company/intuit), [Snapchat](https://leetcode.com/company/snapchat), [Bloomberg](https://leetcode.com/company/bloomberg), [Google](https://leetcode.com/company/google), [eBay](https://leetcode.com/company/ebay), [ByteDance](https://leetcode.com/company/bytedance), [VMware](https://leetcode.com/company/vmware), [Zillow](https://leetcode.com/company/zillow), [Adobe](https://leetcode.com/company/adobe), [Uber](https://leetcode.com/company/uber), [Salesforce](https://leetcode.com/company/salesforce), [Walmart Labs](https://leetcode.com/company/walmart-labs), [Dropbox](https://leetcode.com/company/dropbox), [Cisco](https://leetcode.com/company/cisco), [Tesla](https://leetcode.com/company/tesla), [Goldman Sachs](https://leetcode.com/company/goldman-sachs)

**Related Topics**:  
[Hash Table](https://leetcode.com/tag/hash-table/), [Linked List](https://leetcode.com/tag/linked-list/), [Design](https://leetcode.com/tag/design/), [Doubly-Linked List](https://leetcode.com/tag/doubly-linked-list/)

**Similar Questions**:
* [LFU Cache (Hard)](https://leetcode.com/problems/lfu-cache/)
* [Design In-Memory File System (Hard)](https://leetcode.com/problems/design-in-memory-file-system/)
* [Design Compressed String Iterator (Easy)](https://leetcode.com/problems/design-compressed-string-iterator/)
* [Design Most Recently Used Queue (Medium)](https://leetcode.com/problems/design-most-recently-used-queue/)

## Video Notes

![img349](https://user-images.githubusercontent.com/37560890/170768189-7dd0a7fa-bbc0-4c1d-a706-0cd97d150e23.jpg)
![img351](https://user-images.githubusercontent.com/37560890/170768195-dd9e0945-714c-44fe-a62c-e32e4619f1f4.jpg)
![img353](https://user-images.githubusercontent.com/37560890/170768196-20a88fbd-6c68-4f07-8235-1c14ba7b8d2f.jpg)
![img355](https://user-images.githubusercontent.com/37560890/170768197-ea16d14c-e394-4614-8967-cf9bf1f34c08.jpg)
![img357](https://user-images.githubusercontent.com/37560890/170768199-14f78f80-9a19-427d-81c1-c74a174565d1.jpg)
![img359](https://user-images.githubusercontent.com/37560890/170768201-acee0807-85f1-41df-bfe0-4139bcf1e3b9.jpg)
![img361](https://user-images.githubusercontent.com/37560890/170768204-ada1111c-291a-4900-bd13-2168a71d3163.jpg)
![img363](https://user-images.githubusercontent.com/37560890/170768205-75920a58-4fab-4745-82d5-e7ab4e33dd23.jpg)
![img365](https://user-images.githubusercontent.com/37560890/170768208-0a1b49cb-46a5-41fe-91bd-a5df4b81c8b1.jpg)
![img367](https://user-images.githubusercontent.com/37560890/170768211-44a711db-caba-4f24-84d8-dd70aabf0c88.jpg)
![img369](https://user-images.githubusercontent.com/37560890/170768212-283bb3d6-e0b8-4c1a-a505-dd2653f5ba18.jpg)
![img371](https://user-images.githubusercontent.com/37560890/170768214-87e2603f-f068-4fce-a3b4-1e54893a7083.jpg)
![img373](https://user-images.githubusercontent.com/37560890/170768216-26be4220-4481-48c2-a408-c020c0acbc0d.jpg)
![img375](https://user-images.githubusercontent.com/37560890/170768218-30b202a9-04ea-4bff-8de2-39930186685b.jpg)
![img377](https://user-images.githubusercontent.com/37560890/170768220-36ad4b9d-08f7-4f35-9726-5be1fd2edbe0.jpg)
![img379](https://user-images.githubusercontent.com/37560890/170768221-6522c957-19a6-4ba5-be55-f11a326a7ece.jpg)
![img381](https://user-images.githubusercontent.com/37560890/170768224-2869da13-6865-4ea0-87c1-65b34bbd74f8.jpg)
![img383](https://user-images.githubusercontent.com/37560890/170768228-e49a68e9-a04c-4e98-8b74-9d62e0afdeda.jpg)
![img385](https://user-images.githubusercontent.com/37560890/170768232-74c49d81-8a13-4f58-9620-7b4087422ae7.jpg)
![img387](https://user-images.githubusercontent.com/37560890/170768234-a474d1f1-1c75-4daa-9680-55253ecddb16.jpg)
![img389](https://user-images.githubusercontent.com/37560890/170768236-229132e9-a264-462b-b90d-a344ce6866bb.jpg)
![img391](https://user-images.githubusercontent.com/37560890/170768239-d4709d0d-c20f-4063-869e-09174349b657.jpg)
![img393](https://user-images.githubusercontent.com/37560890/170768242-38691743-b312-4195-a874-eb9c488d1f8f.jpg)
![img395](https://user-images.githubusercontent.com/37560890/170768244-fd0d05f0-cc5e-4e07-9841-344fa6385b0c.jpg)
![img397](https://user-images.githubusercontent.com/37560890/170768247-44416506-9e14-48b3-bdd3-5c0ff0f626bd.jpg)
![img399](https://user-images.githubusercontent.com/37560890/170768249-17897d24-af3a-4df5-a861-00a1ea3c5014.jpg)
![img401](https://user-images.githubusercontent.com/37560890/170768250-f865a411-7cd1-4a30-b6c5-0f0d6d637bb2.jpg)
![img674](https://user-images.githubusercontent.com/106215989/170768794-8ce1795c-967b-4867-b419-21151b59e64e.jpg)
![img676](https://user-images.githubusercontent.com/106215989/170768800-a6fc046e-6a1f-4595-90b6-f594555c6163.jpg)
![img678](https://user-images.githubusercontent.com/106215989/170768805-09703f6c-536a-4ac8-ba1e-10928d3c598e.jpg)
![img680](https://user-images.githubusercontent.com/106215989/170768806-38e6434a-9ae5-456e-aeb4-4d01604b41ca.jpg)
![img682](https://user-images.githubusercontent.com/106215989/170768810-50caffeb-ddec-4b98-9576-f5c9e6a1e0fa.jpg)
![img684](https://user-images.githubusercontent.com/106215989/170768812-978c47ad-0857-4ad2-8cd2-53aeebe8432d.jpg)
![img686](https://user-images.githubusercontent.com/106215989/170768816-a4aad619-ea1d-4340-8da3-4ad43d076b64.jpg)
![img688](https://user-images.githubusercontent.com/106215989/170768818-28a88b7f-6824-47c0-9613-9e09252ca17e.jpg)
![img690](https://user-images.githubusercontent.com/106215989/170768822-eb7d41e4-6026-4046-80ce-33db573367a4.jpg)
![img692](https://user-images.githubusercontent.com/106215989/170768826-fa736b23-4d3c-4d76-93b3-b20ac7f2f248.jpg)
![img694](https://user-images.githubusercontent.com/106215989/170768827-8ef0f123-5b19-47e3-8f58-dd43c5069dae.jpg)
![img696](https://user-images.githubusercontent.com/106215989/170768831-3bb407df-73f2-408b-8acf-1ca80af19351.jpg)


## Note

I usually forgot that I need to store the `<key, value>` pair in the list which is needed when evicting least recently used item.

We'd better write the logic as comments first, then we can find the detailed data structure we need and see if there is any common utility function that we can extract. 

Need to remember the signature of the `splice` function: `toList.splice(toListIterator, fromList, fromListIterator)` is moving the data pointed by the `fromListIterator` from the `fromList` into the position pointed by the `toListIterator` within the `toList`.

## Solution 1.

Use a `list<pair<int, int>> data` to store the key-value pairs, `unordered_map<int, list<pair<int, int>>::iterator> m` to store the mapping from **key** to **the corresponding iterator pointing into data**.

The constructor `LRUCache` is trivial, just storing the `capacity` as member.

The `get` logic is:
* If the `key` cannot be found in `m`, return `-1`.
* Otherwise, move the key-value pair pointed by `m[key]` to the front of `data`. And update `m[key]` to point to the front of `data`. Return the value `data.front().second`.

The `put` logic is:
* Use `get(key)` to test the existance of the `key`.
  * If not found,
    - Emit the last key-value pair, if the `data` storage is full.
    - Then insert the key-value pair to the front of `data` and update `m[key]` accordingly.
  * Otherwise, just update `data.front().second` to be `value`. 

```cpp
// OJ: https://leetcode.com/problems/lru-cache
// Time:
//    LRUCache: O(1)
//    get: O(1)
//    put: O(1)
// Space: O(N)

class LRUCache {
public:

    // Create a node class
    class node
    {
        public:
            // Node key ->val
            int key;
            int val;
        
            // 2 pointers of doubly linked list
            node *next;
            node *prev;
        
            // Define the construcutor for the values initialization
            node(int _key , int _value)
            {
                key = _key;
                val = _value;
            }
    };
    
    // Make the 2 nodes with default values of initilization
    node *head = new node(-1,-1);
    node *tail = new node(-1,-1);
    
    // Define the capacity and map 
    int cap;
    unordered_map<int,node*> m;
    
    
    // Add node 
    void addnode(node * newnode)
    {
        // Assign the temp to the head->next
        node *temp= head->next;
        
        // Update the new node
        newnode->next= temp;
        
        // Update the newnode->prev
        newnode->prev= head;
        
        // Update the head->next
        head->next= newnode;
        
        // Update the temp prev
        temp->prev= newnode;
        
    }
    
    // Define the delete node function
    void deletenode(node *delnode)
    {
        // Delprev pointer will point to the prevnode of the node to be deleted
        node *delprev = delnode->prev;
        
        // Delnext ointer will point to the nextnode of the node to be deleted
        node *delnext= delnode->next;
        
        // Update the delprev
        delprev->next= delnext;
        
        // Update the delnext
        delnext->prev= delprev;
        
    }
    
    // Main LRU cache function just initialize the values
    LRUCache(int capacity) 
    {
        cap= capacity;
        head->next= tail;
        tail->prev= head;
    }
    
    // Get the node
    int get(int key) 
    {
        // If key found in hashmap
        if(m.find(key) != m.end())
        {
            // Get the node corresponding to the key
            node *resnode= m[key];
            
            // Get the interger value
            int res= resnode->val;
            
            // Now erase it from the hashmap
            m.erase(key);
            
            // Delete the resnode due to it's old address
            deletenode(resnode);
            
            // Add the resnode right after the head
            addnode(resnode);
            
            // Assign the new address
            m[key] = head->next;
            
            // Finally return the result
            return res;
        }
        return -1;
    }
    
    void put(int key, int value)
    {
        if(m.find(key) != m.end())
        {
            // If the key exists in the map
            node *existsnode= m[key];
            
            // Now erase the key
            m.erase(key);
            
            // Delete the exisitng key
            deletenode(existsnode);
        }
        
        // Condition to check if the size is full
        if(m.size() == cap)
        {
            // If the size is full then del least recently used
            m.erase(tail->prev->key);
            
            // Now delete that node
            deletenode(tail->prev);
        }
        
        // Now its will be currently accessed node
        addnode(new node(key,value));
        
        // Update in the hashmap
        m[key]= head->next;
    }
};

/**
 * Your LRUCache object will be instantiated and called as such:
 * LRUCache* obj = new LRUCache(capacity);
 * int param_1 = obj->get(key);
 * obj->put(key,value);
 */


```

