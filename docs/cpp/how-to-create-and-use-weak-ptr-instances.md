---
title: 作法：建立和使用 weak_ptr 執行個體
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
ms.openlocfilehash: d7caea7cfd13b3a41a1cd20f88a9914267cf9677
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87187851"
---
# <a name="how-to-create-and-use-weak_ptr-instances"></a>作法：建立和使用 weak_ptr 執行個體

有時候，物件必須儲存一種方法來存取[shared_ptr](../standard-library/shared-ptr-class.md)的基礎物件，而不會導致參考計數遞增。 一般而言，當您在實例之間有迴圈參考時，就會發生這種情況 `shared_ptr` 。

最佳的設計是避免在每次可以時共用指標的擁有權。 不過，如果您必須擁有實例的共用擁有權 `shared_ptr` ，請避免其間的迴圈參考。 當迴圈參考無法避免，或甚至是基於某些原因而偏好時，請使用[weak_ptr](../standard-library/weak-ptr-class.md)給一或多個擁有者提供另一個的弱式參考 `shared_ptr` 。 藉由使用 `weak_ptr` ，您可以建立聯結 `shared_ptr` 至現有相關實例集的，但僅限於基礎記憶體資源仍然有效時。 `weak_ptr`本身不會參與參考計數，因此無法防止參考計數到達零。 不過，您可以使用 `weak_ptr` 來嘗試取得 `shared_ptr` 其初始化所在的新複本。 如果已刪除記憶體，則的 `weak_ptr` bool 運算子會傳回 **`false`** 。 如果記憶體仍然有效，新的共用指標會遞增參考計數，並保證只要 `shared_ptr` 變數留在範圍內，記憶體就會是有效的。

## <a name="example"></a>範例

下列程式碼範例示範 `weak_ptr` 用來確保適當刪除具有迴圈相依性之物件的案例。 當您檢查範例時，假設它只是在考慮替代方案之後才建立的。 `Controller`物件代表電腦進程的某些層面，並獨立運作。 每個控制站都必須能夠隨時查詢其他控制器的狀態，而且每個控制器都包含此用途的私用 `vector<weak_ptr<Controller>>` 。 每個向量都包含迴圈參考，因此 `weak_ptr` 會使用實例，而不是 `shared_ptr` 。

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
Status of 0 = On
Status of 1 = On
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

在實驗中，將向量修改 `others` 為，然後 `vector<shared_ptr<Controller>>` 在輸出中，請注意，當傳回時，不會叫用任何析構函數 `TestRun` 。

## <a name="see-also"></a>另請參閱

[智慧型指標（現代 c + +）](../cpp/smart-pointers-modern-cpp.md)
