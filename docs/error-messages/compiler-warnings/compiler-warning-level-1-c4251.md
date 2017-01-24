---
title: "編譯器警告 (層級 1) C4251 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4251"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4251"
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4251
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : class 'type' 必須有 DLL 介面，才能被為 class 'type2' 的用戶端使用  
  
 若要在以 [\_\_declspec\(dllexport\)](../../cpp/dllexport-dllimport.md) 匯出類別時，將資料毀損的機率減到最低，請確定下列各項：  
  
-   所有靜態資料都是透過從 DLL 匯出的函式存取。  
  
-   沒有任何類別的內嵌方法能夠修改靜態資料。  
  
-   您的類別中不會有任何內嵌的方法會使用 CRT 函式，或是有其他程式庫函式使用靜態資料 \(如需詳細資訊，請參閱[跨 DLL 界限傳遞 CRT 物件時可能發生的錯誤](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)\)。  
  
-   沒有類別的任何方法 \(不管是否內嵌\) 可以使用其中 EXE 和 DLL 內之安裝有靜態資料差異的型別。  
  
 透過定義用虛擬函式定義類別的 DLL 和可呼叫以具現化的函式，並刪除型別的物件，您可以避免匯出類別。然後就直接在型別上呼叫虛擬函式。  
  
 如需匯出範本的詳細資訊，請參閱 [http:\/\/support.microsoft.com\/default.aspx?scid\=KB;EN\-US;168958](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958)。  
  
 如果您要衍生自 Standard C\+\+ 程式庫中的型別、編譯偵錯版本 \(**\/MTd**\)，且編譯器錯誤訊息參考 \_Container\_base，則可以忽略 C4251。  
  
```  
// C4251.cpp  
// compile with: /EHsc /MTd /W2 /c  
#include <vector>  
using namespace std;  
class Node;  
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251  
```