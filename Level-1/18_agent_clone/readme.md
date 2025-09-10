

## Cloning/copying agents
Agent cloning OpenAI Agents SDK mein ek aisa process hai jismein aap ek existing agent ki copy banate hain aur uske kuch properties ko modify kar sakte hain, jabke original agent ki configuration wahi rehti hai. Ye clone() method se hota hai, jo ek naya agent instance return karta hai, jismein aap original agent ke base par changes kar sakte hain bina asal agent ko affect kiye.

* clone() method ek shallow copy banata hai, yani agent ki configuration (jaise name, instructions, model, tools, aur handoffs) copy hoti hai, lekin mutable cheezein (jaise tools ya handoffs ki list) share hoti hain jab tak aap nayi list na dein.
* Istemaal: Cloning se aap ek agent ke alag versions bana sakte hain, masalan different instructions ya model ke sath, testing ya specific tasks ke liye, bina original agent ko change kiye.

OpenAI Agents SDK mein clone() method shallow copy use karta hai. Yani agent ke mutable attributes (jaise tools ya handoffs ki lists) original aur cloned agent mein share hote hain.

### Shallow Copy:

* Shallow copy ek naya object banata hai, lekin ismein original object ke references (pointers) copy hote hain, na ke actual data. Yani agar original object mein koi mutable items (jaise lists ya dictionaries) hain, to dono objects (original aur copy) unhi mutable items ko share karte hain.
* Kaise hota hai?: Shallow copy sirf top-level structure ko copy karta hai, lekin nested objects (objects ke andar objects) ka reference wahi rehta hai.
```bash
import copy

original = [1, 2, [3, 4]]
shallow = copy.copy(original)

shallow[2][0] = 99
print(original)  # [1, 2, [99, 4]] (original bhi change ho gaya)
print(shallow)   # [1, 2, [99, 4]]
```
* Yahan shallow[2] wali list ka reference original se share hota hai, isliye nested list mein change dono jagah dikhta hai.
* Kab use karen?: Jab aapko sirf top-level structure copy karni ho aur nested objects ko share karna theek ho.

### Deep Copy
* Kya hai?: Deep copy ek naya object banata hai aur original object ke saare data ko recursively copy karta hai, yani nested objects bhi naye banaye jaate hain. Copy aur original bilkul alag hote hain, koi shared reference nahi hota.
* Kaise hota hai?: Deep copy poori data structure ko duplicate karta hai, chahe kitne bhi nested objects hon.
```bash
import copy

original = [1, 2, [3, 4]]
deep = copy.deepcopy(original)

deep[2][0] = 99
print(original)  # [1, 2, [3, 4]] (original nahi badla)
print(deep)      # [1, 2, [99, 4]]
```
* Yahan deep[2] mein change sirf copy mein hota hai, original wahi rehta hai kyunke nested list bhi alag copy hui.
* Kab use karen?: Jab aapko original object se bilkul independent copy chahiye, jismein koi bhi change original ko affect na kare.

#### Difference
* Shallow Copy: Sirf top-level copy karta hai, nested objects share hote hain. Fast hai lekin changes original ko bhi affect kar sakte hain.
8 Deep Copy: Poora object aur uske saare nested objects copy hote hain. Thoda slow hai lekin original aur copy bilkul alag hote hain.

