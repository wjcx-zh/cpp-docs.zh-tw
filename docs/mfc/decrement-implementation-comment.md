---
title: "// 實作註解 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "註解, 實作註解"
  - "註解, MFC"
  - "MFC 原始程式檔中的實作註解"
  - "MFC 原始程式檔, 實作註解"
ms.assetid: 4d799c07-8e71-4a6b-90ab-8282d6ff48ce
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# // 實作註解
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`// Implementation` 部分是所有 MFC 類別宣告的重要部分。  
  
 這個工作區房屋所有實作詳細資料。  成員變數和成員函式會出現在這個部分。  所有在這一行下方 MFC 在未來版本中變更。  除非您無法使用它，您不應依賴詳細資料新增至 `// Implementation` 這一行下方。  此外，在實作行下宣告的成員未記載，不過，某些實作技術提示中討論。  虛擬函式覆寫在基底類別中位於區段，無論部分基底類別函式定義，，因為這個事實函式覆寫基底類別實作會被視為實作詳細資料。  一般來說，這些成員不一定會保護，不過，。  
  
 從列於 `// Implementation` 註解下宣告的成員可宣告為 **public**、 `protected`或 `private`的 [註解的範例](../mfc/an-example-of-the-comments.md) 下的 `CStdioFile` 的注意事項。  因為它們可能會在未來，變更您應該小心地只使用這些成員。  宣告成員的群組做為 **public** 的可能需要為類別庫所實作才能正確運作。  不過，這並不表示您可以安全地使用成員很宣告。  
  
> [!NOTE]
>  您可能會發現其他類型的註解中或在 `// Implementation` 註解下上。  在任何情況下，它們會描述在其下宣告的成員類型。  如果使用者在 `// Implementation` 註解下發生，您應該假設，成員在 MFC 未來的版本中可能會變更。  
  
## 請參閱  
 [使用 MFC 原始程式檔](../mfc/using-the-mfc-source-files.md)   
 [註解的範例](../mfc/an-example-of-the-comments.md)   
 [\/\/ 建構函式註解](../mfc/decrement-constructors-comment.md)   
 [\/\/ 屬性註解](../mfc/decrement-attributes-comment.md)   
 [\/\/ 作業註解](../mfc/decrement-operations-comment.md)   
 [\/\/ 可覆寫函式註解](../mfc/decrement-overridables-comment.md)