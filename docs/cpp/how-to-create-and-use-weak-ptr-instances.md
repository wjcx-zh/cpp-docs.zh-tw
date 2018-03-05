---
title: "如何： 建立和使用 weak_ptr 執行個體 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3e51e523540e14905bef17edd52205c4d2102afa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-and-use-weakptr-instances"></a>如何：建立和使用 weak_ptr 執行個體
有時物件必須儲存存取的基礎物件的方法`shared_ptr`而不會造成參考計數遞增。 一般而言，這種情況您有會發生之間有循環參考`shared_ptr`執行個體。  
  
 最好的設計是儘可能避免共用擁有權的指標。 不過，如果您必須有共用的擁有權`shared_ptr`執行個體，避免兩者之間有循環參考。 當有循環參考不可避免的或甚至比基於某些原因，請使用`weak_ptr`讓一或多個擁有者的弱式參考另一個`shared_ptr`。 使用`weak_ptr`，您可以建立`shared_ptr`聯結至現有集合的相關執行個體，但僅限於基礎的記憶體資源是否仍然有效。 A`weak_ptr`本身不會參與參考計數，因此，它無法防止的參考計數，送到零。 不過，您可以使用`weak_ptr`來嘗試取得一份新`shared_ptr`與它已初始化。 如果記憶體已被刪除， **bad_weak_ptr**擲回例外狀況。 如果仍然有效的記憶體，則新的共用的指標會遞增參考計數，而且不保證記憶體才有效，只要`shared_ptr`變數會保持在範圍內。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範案例其中`weak_ptr`用來確保適當刪除具有循環相依性物件。 當您檢查此範例，假設它已建立在考量替代方案之後，才。 `Controller`物件代表某方面的機器的處理程序，以及它們是獨立運作。 每個控制站必須能夠在任何時候，查詢的其他控制站狀態，每一個包含私用`vector<weak_ptr<Controller>>`針對此目的。 每個向量中包含循環參考，因此`weak_ptr`而不是使用執行個體`shared_ptr`。  
  
 [!code-cpp[stl_smart_pointers#222](../cpp/codesnippet/CPP/how-to-create-and-use-weak-ptr-instances_1.cpp)]  
  
```Output  
Creating Controller0Creating Controller1Creating Controller2Creating Controller3Creating Controller4push_back to v[0]: 1push_back to v[0]: 2push_back to v[0]: 3push_back to v[0]: 4push_back to v[1]: 0push_back to v[1]: 2push_back to v[1]: 3push_back to v[1]: 4push_back to v[2]: 0push_back to v[2]: 1push_back to v[2]: 3push_back to v[2]: 4push_back to v[3]: 0push_back to v[3]: 1push_back to v[3]: 2push_back to v[3]: 4push_back to v[4]: 0push_back to v[4]: 1push_back to v[4]: 2push_back to v[4]: 3use_count = 1Status of 1 = OnStatus of 2 = OnStatus of 3 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 2 = OnStatus of 3 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 1 = OnStatus of 3 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 1 = OnStatus of 2 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 1 = OnStatus of 2 = OnStatus of 3 = OnDestroying Controller0Destroying Controller1Destroying Controller2Destroying Controller3Destroying Controller4Press any key  
```  
  
 做一個試驗，修改向量`others`是`vector<shared_ptr<Controller>>`，在輸出中，注意沒有解構函式會叫用時`TestRun`傳回。  
  
## <a name="see-also"></a>請參閱  
 [智慧型指標](../cpp/smart-pointers-modern-cpp.md)