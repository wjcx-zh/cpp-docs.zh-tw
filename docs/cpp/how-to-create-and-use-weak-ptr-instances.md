---
title: 如何： 建立和使用 weak_ptr 執行個體 |Microsoft Docs
ms.custom: how-to
ms.date: 07/12/2018
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fe982762c6e6c44b8f1923d27779bcfd6140225
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087696"
---
# <a name="how-to-create-and-use-weakptr-instances"></a>如何：建立和使用 weak_ptr 執行個體

有時候物件必須儲存存取的基礎物件的方法`shared_ptr`而不會造成參考計數遞增。 一般而言，這種情況發生時有循環參考之間`shared_ptr`執行個體。

最好的設計是儘可能避免共用的指標擁有。 不過，如果您必須有共用的擁有權`shared_ptr`情況下，避免兩者之間的循環參考。 當循環參考無法避免，或者甚至比基於某些原因，請使用`weak_ptr`提供一或多個擁有者之間的弱式參考`shared_ptr`。 藉由使用`weak_ptr`，您可以建立`shared_ptr`以聯結相關的執行個體，但僅限於一組現有的基礎記憶體資源是否仍然有效。 A`weak_ptr`本身不會參與參考計數，因此，它無法防止參考計數變成零。 不過，您可以使用`weak_ptr`來嘗試取得一份新`shared_ptr`與初始化。 如果已刪除的記憶體，`bad_weak_ptr`擲回例外狀況。 如果記憶體仍然有效，新的共用的指標會遞增參考計數，並保證記憶體才有效，只要`shared_ptr`變數保持在範圍內。

## <a name="example"></a>範例

下列程式碼範例所示的範例位置`weak_ptr`用來確保正確刪除有循環相依性的物件。 當您檢查的範例，假設它建立在考慮替代方案之後，才。 `Controller`物件代表機器程序的某些層面，以及其個別運作。 每個控制站必須能夠隨時查詢其他控制器的狀態，而且每個包含私用`vector<weak_ptr<Controller>>`針對此目的。 每個向量包含循環參考，因此`weak_ptr`執行個體來取代`shared_ptr`。

[!code-cpp[stl_smart_pointers#222](../cpp/codesnippet/CPP/how-to-create-and-use-weak-ptr-instances_1.cpp)]

```Output
Creating Controller0
Creating Controller1
Creating Controller2
Creating Controller3
Creating Controller4
push_back to v[0]: 1
push_back to v[0]: 2
push_back to v[0]: 3
push_back to v[0]: 4
push_back to v[1]: 0
push_back to v[1]: 2
push_back to v[1]: 3
push_back to v[1]: 4
push_back to v[2]: 0
push_back to v[2]: 1
push_back to v[2]: 3
push_back to v[2]: 4
push_back to v[3]: 0
push_back to v[3]: 1
push_back to v[3]: 2
push_back to v[3]: 4
push_back to v[4]: 0
push_back to v[4]: 1
push_back to v[4]: 2
push_back to v[4]: 3
use_count = 1
Status of 1 = On
Status of 2 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 2 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 1 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = O
nStatus of 1 = On
Status of 2 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 1 = On
Status of 2 = On
Status of 3 = On
Destroying Controller0
Destroying Controller1
Destroying Controller2
Destroying Controller3
Destroying Controller4
Press any key
```

做一個試驗，修改向量`others`要`vector<shared_ptr<Controller>>`，然後在輸出中，請注意任何解構函式會叫用時`TestRun`傳回。

## <a name="see-also"></a>另請參閱

[智慧型指標](../cpp/smart-pointers-modern-cpp.md)