---
title: test post
layout: post
categories: Personal
---
This is a test

```swift
import Foundation

class ItemsViewModel {
    var items: [Item] = []
    var error: Error?
    var refreshing = false
    
    private let dataManager: DataManager
    init(dataManager: DataManager) {
        self.dataManager = dataManager
    }
    
    func fetch(completion: @escaping () -> Void) {
        refreshing = true
        dataManager.fetchItems { [weak self] (items, error) in
            self?.items = items ?? []
            self?.error = error
            self?.refreshing = false
            completion()
        }
    }
}
```

