---
title: 編譯器警告 (層級 1) C4251
ms.date: 11/04/2016
f1_keywords:
- C4251
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
ms.openlocfilehash: d2fff1d2f30c4ac80af6d5b9ca452fa5f30f5a15
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207346"
---
# <a name="compiler-warning-level-1-c4251"></a>編譯器警告 (層級 1) C4251

'identifier': 類別 'type' 必須有 dll 介面，可供類別 'type2' 的用戶端

若要匯出的類別時，將資料損毀的可能性降至最低[__declspec （dllexport)](../../cpp/dllexport-dllimport.md)，請確認：

- 所有靜態資料是透過從 DLL 匯出的函式的存取。

- 沒有內嵌的方法，您的類別可以修改靜態資料。

- 沒有內嵌的方法，您的類別使用的 CRT 函式或其他程式庫函式會使用靜態資料 (請參閱[潛在錯誤物件跨 DLL 界限傳遞 CRT](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)如需詳細資訊)。

- 您的類別沒有任何方法 (不管內嵌) 可以用來使用 EXE 和 DLL 中的具現化其中有靜態資料差異的類型。

您可以避免匯出類別所定義的 DLL，定義具有虛擬函式，類別和函式您可以呼叫來具現化和刪除的物件類型。  然後，您就可以再呼叫虛擬函式類型。

如果您衍生自中的型別，就可以忽略 C4251C++編譯的偵錯版本的標準程式庫 (**/MTd**) 和其中的編譯器錯誤訊息指的是 _Container_base。

```cpp
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251
```