# sample-mutation-observer
A sample implementation of MutationObserver to listen to DOM event changes such as node added or removed


## Example usage
- Copy and paste the code to browser console to debug new node added or removed events
```javascript
const childNodeChangeListener = (targetNode) => {
    const mutationListenerCallback = (mutationList, observer) => {
        for (const mutation of mutationList) {
            if (mutation.type === 'childList') {
                for (const addedNode of mutation.addedNodes) {
                    if (addedNode.nodeType === Node.ELEMENT_NODE) {
                        debugger
                        console.log('A child node has been added:', addedNode);
                    }
                }
            }
            for (const removedNode of mutation.removedNodes) {
                if (removedNode.nodeType === Node.ELEMENT_NODE) {
                    debugger
                    console.log('A child node has been removed:', removedNode);
                }
            }
        }
    }
    
    const observer = new MutationObserver(mutationListenerCallback)
    
    const config = { childList: true }
    
    observer.observe(targetNode, config)
}

const targetNode = document.body
// const targetNode = document.getElementById("element-id")

childNodeChangeListener(targetNode)
```


## References
- Learn more about MutationObserver if you want a more specific event observer
    - https://developer.mozilla.org/en-US/docs/Web/API/MutationObserver
	- https://developer.mozilla.org/en-US/docs/Web/API/MutationRecord
