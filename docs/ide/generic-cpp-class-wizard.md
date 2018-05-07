---
title: 泛型 c + + 類別精靈 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.class.generic
dev_langs:
- C++
helpviewer_keywords:
- Generic C++ Class Wizard [C++]
ms.assetid: aa95be9e-fc1b-45db-a11d-0d32c4929077
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43e86a4047ef025f49dd01eda90f324623a90752
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="generic-c-class-wizard"></a>泛型 C++ 類別精靈
專案中加入泛型 c + + 類別。 此類別無法繼承自 ATL 或 MFC。  
  
 **類別名稱**  
 設定新的類別名稱。  
  
 **.h 檔案**  
 設定新類別的標頭檔的名稱。 根據預設，這個名稱根據您在中提供的名稱**類別名稱**。 若要將標頭檔儲存到您選擇的位置，或類別宣告附加至現有的檔案，按一下省略符號按鈕 (**...**).如果您指定現有的檔案，當您按一下**完成**，精靈會提示您指定是否要在類別宣告附加至檔案的內容。 若要附加的宣告，請按一下**是**; 若要返回精靈並指定其他檔案名稱，請按一下**否**。  
  
 **.cpp 檔案中**  
 設定新的類別的實作檔名稱。 根據預設，這個名稱根據您在中提供的名稱**類別名稱**。 若要將實作檔案儲存到您選擇的位置，或類別定義附加至現有的檔案，按一下省略符號按鈕 (**...**).如果您指定現有的檔案，當您按一下**完成**，精靈會提示您指定的類別定義是否應該附加至檔案的內容。 若要附加的定義，請按一下**是**; 若要返回精靈並指定其他檔案名稱，請按一下**否**。  
  
 **基底類別**  
 設定新的類別的基底類別。  
  
 **存取權**  
 集合的存取權的基底類別成員的新類別。 存取修飾詞是存取的指定的其他類別所擁有的類別成員函式層級的關鍵字。 如需如何指定權限的詳細資訊，請參閱[成員存取控制](../cpp/member-access-control-cpp.md)。 根據預設，類別存取層級設定為`public`。  
  
-   `public`  
  
-   `protected`  
  
-   `private`  
  
-   **預設**（會產生任何存取修飾詞）。  
  
 **虛擬解構函式**  
 指定類別的解構函式是否為虛擬。 使用虛擬解構函式可協助確保，當在衍生類別的執行個體已刪除時，會呼叫正確的解構函式。  
  
 **內嵌**  
 標頭檔中產生的類別建構函式和內嵌函式的類別定義。  
  
 **受管理**  
 選取時，將 managed 的類別和標頭檔中。 清除時，將原生類別和標頭檔中。  
  
## <a name="see-also"></a>另請參閱  
 [新增泛型 C++ 類別](../ide/adding-a-generic-cpp-class.md)