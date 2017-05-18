---
title: "編譯器警告 （層級 1） C4251 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4251
dev_langs:
- C++
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: b75c3e6c93c0963a692b210b158339ea5e9eacac
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4251"></a>編譯器警告 (層級 1) C4251
'identifier': 類別 'type' 必須有 'type2' 類別的用戶端所使用的 dll 介面  
  
 若要匯出的類別時，將資料損毀的可能性降至最低[__declspec （dllexport)](../../cpp/dllexport-dllimport.md)，請確認︰  
  
-   所有靜態資料是透過從 DLL 匯出的函式的存取。  
  
-   您的類別沒有內嵌的方法可以修改靜態資料。  
  
-   沒有內嵌的方法，您的類別使用 CRT 函式或其他程式庫函式使用靜態資料 (請參閱[潛在錯誤物件跨 DLL 界限傳遞 CRT](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)如需詳細資訊)。  
  
-   沒有類別的方法 (不管內嵌) 可以使用型別上的 EXE 和 DLL 中具現化具有靜態資料的差異。  
  
 您可以避免匯出類別所定義的 DLL，定義具有虛擬函式、 類別和函式您可以呼叫來具現化和刪除物件的型別。  然後，您就可以再呼叫虛擬函式型別上。  
  
 如需匯出範本的詳細資訊，請參閱[http://support.microsoft.com/default.aspx?scid=KB;EN-US;&16895;8](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958)。  
  
 如果您衍生自 c + + 標準程式庫，編譯偵錯版本中的型別，就可以忽略 C4251 (**/MTd**) 和 _Container_base 其中是指編譯器錯誤訊息。  
  
```  
// C4251.cpp  
// compile with: /EHsc /MTd /W2 /c  
#include <vector>  
using namespace std;  
class Node;  
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251  
```
