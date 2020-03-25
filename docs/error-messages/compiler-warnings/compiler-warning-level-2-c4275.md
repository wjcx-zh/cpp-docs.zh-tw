---
title: 編譯器警告 (層級 2) C4275
ms.date: 02/08/2019
f1_keywords:
- C4275
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
ms.openlocfilehash: ad12c1c27006a57c8339e9dad82e4d8e1a239a6e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161993"
---
# <a name="compiler-warning-level-2-c4275"></a>編譯器警告 (層級 2) C4275

> 做為 DLL 介面類別別 '*class_2*' 基底使用的非 DLL 介面類別別 '*class_1*'

匯出的類別衍生自未匯出的類別。

若要在使用[__declspec （dllexport）](../../cpp/dllexport-dllimport.md)匯出類別時，將資料損毀的可能性降到最低，請確定：

- 您所有的靜態資料都是透過從 DLL 匯出的函式來存取。

- 您類別的任何內嵌方法都不能修改靜態資料。

- 類別的任何內嵌方法都不會使用 CRT 函式或其他使用靜態資料的程式庫函數。

- 沒有任何內嵌類別函式使用 CRT 函式或其他程式庫函式，您可以在其中存取靜態資料。

- 您的類別沒有任何方法（不論內嵌為何）可以使用類型，其中 EXE 和 DLL 中的具現化具有靜態資料差異。

您可以藉由定義定義具有虛擬函式之類別的 DLL 來避免匯出類別，以及您可以呼叫來具現化和刪除型別物件的函式。  然後您就可以在型別上呼叫虛擬函式。

如果您是從C++ C++標準程式庫中的型別衍生、編譯 debug release （ **/MTd**），而且編譯器錯誤訊息參考 `_Container_base`，則在視覺效果中可以忽略 C4275。

```cpp
// C4275.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275
```
