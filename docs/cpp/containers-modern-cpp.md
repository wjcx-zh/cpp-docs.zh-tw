---
title: "容器 （現代 c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 6e10b758-e928-4827-9c3f-86cafe54bf5b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4fc8bbc3a983e6fa50e4ae5e8590e1f1de37f02f
ms.sourcegitcommit: ff9bf140b6874bc08718674c07312ecb5f996463
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="containers-modern-c"></a>容器 (現代 C++)  
  
根據預設，使用[向量](../standard-library/vector-class.md)做為慣用的循序容器，在 c + +。 這相當於`List<T>`以.NET 語言。  
  
```cpp  
vector<string> apples;  
apples.push_back("Granny Smith");  
```  
  
使用[對應](../standard-library/map-class.md)(不`unordered_map`) 做為預設關聯容器。 使用[設定](../standard-library/set-class.md)， [multimap](../standard-library/multimap-class.md)，和[multiset](../standard-library/multiset-class.md)變質 & 多情況下。  
  
```cpp  
map<string, string> apple_color;  
// ...  
apple_color["Granny Smith"] = "Green";  
```  
  
當需要效能最佳化時，請考慮使用：  
  
1.  [陣列](../standard-library/array-class-stl.md)輸入內嵌很重要的比方說，做為成員。  
  
2.  例如，未排序關聯容器[unordered_map](../standard-library/unordered-map-class.md)。 這些具有額外負荷較低的每個元素，並定時查閱，但它們可能不容易使用正確且有效率。  
  
3.  排序`vector`。 如需詳細資訊，請參閱[演算法](../cpp/algorithms-modern-cpp.md)。  
  
不使用 C 樣式的陣列。 適用於較舊需要直接存取資料的 Api，使用存取子方法例如`f(vec.data(), vec.size());`改為。  
  
如需容器的詳細資訊，請參閱[c + + 標準程式庫容器](../standard-library/stl-containers.md)。  
  
## <a name="see-also"></a>請參閱  
 [歡迎回到 c + +](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C + + 語言參考](../cpp/cpp-language-reference.md)   
 [C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)
