---
title: "泛型 C++ 類別精靈 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.class.generic"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "泛型 C++ 類別精靈 [C++]"
ms.assetid: aa95be9e-fc1b-45db-a11d-0d32c4929077
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 泛型 C++ 類別精靈
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將泛型 C\+\+ 類別新增至專案。  類別不會自 ATL 或 MFC 繼承。  
  
 **類別名稱**  
 設定新類別的名稱。  
  
 **.h 檔案**  
 為新類別設定標頭檔 \(Header File\) 名稱。  依照預設，這個名稱會根據在 \[類別名稱\] 中提供的名稱來命名。  若要將標頭檔儲存至您選擇的位置，或將類別宣告附加至現有的檔案，請按一下省略按鈕 \(**...**\)。  如果您指定現有的檔案，則當您按一下 \[**完成**\] 時，精靈會提示您指定是否要將類別宣告附加至檔案的內容。  若要附加宣告，按一下 \[**是**\]。若要回到精靈並指定另一個檔案名稱，按一下 \[**否**\]。  
  
 **.cpp 檔**  
 設定新類別的實作檔的名稱。  依照預設，這個名稱會根據在 \[類別名稱\] 中提供的名稱來命名。  若要將實作檔儲存至您選擇的位置，或將類別定義附加至現有的檔案，請按一下省略按鈕 \(**...**\)。  如果您指定現有的檔案，則當您按一下 \[**完成**\] 時，精靈會提示您指定是否要將類別定義附加至檔案的內容。  若要附加定義，按一下 \[**是**\]。若要回到精靈並指定另一個檔案名稱，按一下 \[**否**\]。  
  
 **基底類別**  
 設定新類別的基底類別 \(Base Class\)。  
  
 **存取權**  
 設定新類別之基底類別成員的存取權限。  存取修飾詞 \(Modifier\) 是指定其他類別對類別成員函式之存取層級的關鍵字。  如需關於如何指定存取的詳細資訊，請參閱[成員存取控制](../cpp/member-access-control-cpp.md).  類別存取層級預設為 `public`。  
  
-   `public`  
  
-   `protected`  
  
-   `private`  
  
-   **預設** \(未產生任何存取修飾詞。\)  
  
 **虛擬解構函式**  
 指定類別解構函式是否為虛擬的。  使用虛擬解構函式可確保當刪除衍生類別的執行個體時會呼叫正確的解構函式。  
  
 **內嵌**  
 產生類別建構函式和類別定義，做為標頭檔中的內嵌函式。  
  
 **Managed**  
 選取後，會加入 Managed 類別和標頭檔。  取消選取時，會加入原生類別和標頭檔。  
  
## 請參閱  
 [加入泛型 C\+\+ 類別](../ide/adding-a-generic-cpp-class.md)