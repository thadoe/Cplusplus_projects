// My solution for " Least Recently Used CLRU)" Cache problem from Hackerrank C++ 
// refer to https://www.hackerrank.com/challenges/abstract-classes-polymorphism/problem

class LRUCache : public Cache{
    public:
        LRUCache (int a){cp = a;
        }
        void set (int k , int v){
            Node* n;  //pointer to new node objects 
            if(mp.empty()){
                n = new Node(k,v);
                tail = n;
                head = n; 
                mp[k] = n;
            }else{
                
                auto it = mp.find(k); // iterator for map
                //it ->second-> value = v;                      // if key is found, set the vale of node at key
                if (it != mp.end()){                            // if k is found 
                    it ->second-> value = v; 
                    if (it -> second == head){                  // found  at head, do nothing 
                        return;
                    }
                    else if (it -> second == tail){            // if k is found at tail node 
                            tail = tail->prev;                 // adjust tail pointer 
                            it -> second->prev->next = NULL;   // adjust second last node to be last node 
                    }else { // found in between 
                            it -> second -> prev -> next = it -> second -> next;        // adjust previous and next nodes of node k        
                        }

                        head -> prev = it ->second;
                        it -> second-> prev = NULL;
                        it -> second -> next = head;
                        head = it -> second ;
                
                    }   

                 else { // no node is found with k value 
                    n = new Node (NULL,head, k,v);
                    head->prev = n;
                    head= n;
                    mp[k] = n;

                 }
                if ( mp.size() > cp){
                        Node* delete_node = tail;
                        mp.erase(tail->key);
                        tail = tail -> prev;
                        tail -> next= NULL;
                        free(delete_node);
                        }
                 }
        }
        int get(int k) {
            auto itr = mp.find(k);
            if (itr != mp.end()){
                return itr ->second->value;
            } else {
                return -1;            
                }
            
        }
};
