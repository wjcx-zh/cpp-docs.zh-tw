---
title: 編譯器警告 （層級 2） C4275 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4275
dev_langs:
- C++
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a5d2a3cd7c4b937f8bee1b8f8e37e0619cc224ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-2-c4275"></a>編譯器警告 (層級 2) C4275
非 DLL 介面 classkey 'identifier' 做為基底 DLL 介面 classkey 'identifier'  
  
 匯出的類別衍生自未匯出的類別。  
  
 若要匯出的類別時，將資料損毀的可能性降至最低[__declspec （dllexport)](../../cpp/dllexport-dllimport.md)，請確認：  
  
-   所有靜態資料是透過從 DLL 匯出的函式存取。  
  
-   沒有內嵌的方法，您的類別可以修改靜態資料。  
  
-   沒有內嵌的方法，您的類別使用 CRT 函式或其他程式庫函式會使用靜態資料。  
  
-   沒有內嵌的類別函式會使用 CRT 函式或其他程式庫函式中，您在其中，例如，存取靜態資料。  
  
-   您的類別沒有任何方法 (不論內嵌) 可以用來使用在 EXE 和 DLL 中的具現化其中有靜態資料差異的類型。  
  
 您可以避免匯出定義的 DLL，定義虛擬函式，類別和函式您可以呼叫來具現化和刪除物件類型的類別。  然後，您就可以再呼叫虛擬函式類型上。  
  
 如需有關匯出範本的詳細資訊，請參閱[ http://support.microsoft.com/default.aspx?scid=KB;EN-US; 168958](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958)。  
  
 C4275 可以忽略 Visual c + + 中，如果您衍生自 c + + 標準程式庫、 編譯偵錯版本中的型別 (**/MTd**) 及編譯器錯誤訊息，其中 _Container_base 是指。  
  
```  
// C4275.cpp  
// compile with: /EHsc /MTd /W2 /c  
#include <vector>  
using namespace std;  
class Node;  
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275  
```