---
title: 編譯器警告 (層級 1) C4251
ms.date: 04/21/2020
f1_keywords:
- C4251
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
ms.openlocfilehash: 9f261d3deb7f1cac8cd5c60b920e0be49bc8b7a6
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032326"
---
# <a name="compiler-warning-level-1-c4251"></a>編譯器警告 (層級 1) C4251

> '*類型*' : 類別 '*類型 1*' 需要有 dll 介面,以便類別 '類型*2'* 的用戶端使用 dll 介面

## <a name="remarks"></a>備註

為了在匯出聲明為[__declspec(dllexport)](../../cpp/dllexport-dllimport.md)的類時,將數據損壞的可能性降至最低,請確保:

- 所有靜態數據都通過從 DLL 匯出的函數進行訪問。

- 類的內聯方法無法修改靜態數據。

- 類中聯方法不使用CRT函數或使用靜態數據的其他庫函數。 關於詳細資訊,請參閱透過[DLL 邊界傳遞 CRT 物件的潛在錯誤](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)。

- 類(無論是否內聯)的函數中任何方法都無法使用 EXE 和 DLL 中的實例化具有靜態數據差異的類型。

在從 DLL 匯出類時,可以避免問題:將類定義為具有虛擬函數,以及實例化和刪除類型物件的函數。 然後,您可以調用類型的虛擬函數。

如果類派生自標準庫中C++類型,編譯調試版本 **(/MTd),** 以及編譯器錯誤`_Container_base`消息引用 的位置,則可以忽略 C4251。

## <a name="example"></a>範例

此示例匯出派生自`VecWrapper``std::vector`的專用類。

```cpp
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllexport) VecWrapper : vector<Node *> {};   // C4251
```
