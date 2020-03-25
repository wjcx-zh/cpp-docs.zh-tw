---
title: 編譯器警告 (層級 1) C4251
ms.date: 11/04/2016
f1_keywords:
- C4251
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
ms.openlocfilehash: 8a723b7ce7fc79fb6be9c9dd2b500631098622b0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163215"
---
# <a name="compiler-warning-level-1-c4251"></a>編譯器警告 (層級 1) C4251

' identifier '：類別 ' type ' 必須有 dll 介面，才能由 ' type2 ' 類別的用戶端使用

若要在使用[__declspec （dllexport）](../../cpp/dllexport-dllimport.md)匯出類別時，將資料損毀的可能性降到最低，請確定：

- 您所有的靜態資料都可以透過從 DLL 匯出的函式來存取。

- 您類別的任何內嵌方法都不能修改靜態資料。

- 您的類別中沒有任何內嵌方法使用 CRT 函式或其他程式庫函式使用靜態資料（如需詳細資訊，請參閱[跨 DLL 界限傳遞 CRT 物件的潛在錯誤](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)）。

- 您的類別沒有任何方法（不論內嵌為何）可以使用類型，其中 EXE 和 DLL 中的具現化具有靜態資料差異。

您可以藉由定義定義具有虛擬函式之類別的 DLL 來避免匯出類別，以及您可以呼叫來具現化和刪除型別物件的函式。  然後您就可以在型別上呼叫虛擬函式。

如果您是從C++標準程式庫中的類型衍生、編譯 debug 版本（ **/MTd**），以及編譯器錯誤訊息參考 _Container_base，則可以忽略 C4251。

```cpp
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251
```
