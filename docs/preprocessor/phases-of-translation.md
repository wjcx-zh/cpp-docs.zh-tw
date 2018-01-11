---
title: "轉譯階段 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- translation phases
- preprocessor, translation
- translation, compiler process
- preprocessor
- file translation [C++], compiler process
- files [C++], translation
ms.assetid: a7f7a8c9-e8ba-4321-9e50-ebfbbdcce9db
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 22d73156d4f03a32bd9aa382dd0cc610f8a5f03f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="phases-of-translation"></a>轉譯階段
C 和 C++ 程式是由一個或多個原始程式檔所組成，每個原始程式檔會包含一些程式文字。 原始程式檔連同其 include 檔 (使用 `#include` 前置處理器指示詞所包含的檔案) 稱為「轉譯單位」，但不包括條件式編譯指示詞 (例如 `#if`) 所移除的程式碼區段。  
  
 原始程式檔可以在不同時間轉譯，實際上通常只會轉譯過時的檔案。 轉譯的轉譯單位可以處理為不同的目的檔或目的碼程式庫。 然後這些各自轉譯的轉譯單位會彼此連結，構成可執行程式或動態連結程式庫 (DLL)。  如需可以用做為連結器輸入檔案的詳細資訊，請參閱[LINK 輸入檔](../build/reference/link-input-files.md)。  
  
 轉譯單位可能使用下列方式進行通訊：  
  
-   呼叫具有外部連結的函式。  
  
-   呼叫具有外部連結的類別成員函式。  
  
-   直接修改具有外部連結的物件。  
  
-   直接修改檔案。  
  
-   處理序間通訊 (只適用於 Microsoft Windows 應用程式)。  
  
 下列清單將描述編譯器轉譯檔案的各個階段：  
  
 *字元對應*  
 原始程式檔中的字元會對應至內部來源表示。 在這個階段中，三併詞序列會轉換成單一字元的內部表示。  
  
 *行接合*  
 所有的行結尾是反斜線 (**\\**) 且後面緊接著新行字元加入形成邏輯程式敘述行從實體的多行的原始程式檔中的下一行。 除非原始程式檔是空的，否則必須以前面未加上反斜線的新行字元結尾。  
  
 *Token 化*  
 原始程式檔會分成前置處理語彙基元和空白字元。 原始程式檔中的每一個註解會分別取代為一個空白字元。 新行字元會加以保留。  
  
 *前置處理*  
 前置處理指示詞會執行，而且巨集會展開至原始程式檔。 `#include` 陳述式會在任何包含的文字上，叫用以上述三個轉譯步驟開始的轉譯。  
  
 *字元集對應*  
 所有來源字元集成員和逸出序列都會轉換成它們在執行字元集中的相等用法。 在 Microsoft C 和 C++ 中，來源和執行字元集都是 ASCII。  
  
 *字串串連*  
 所有相鄰字串和寬字串常值都會串連。 例如，`"String " "concatenation"` 會成為 `"String concatenation"`。  
  
 *轉譯*  
 所有語彙基元都會經過語法和語意上的分析，而且這些語彙基元會轉換成目的碼。  
  
 *連結*  
 所有外部參考都會加以解析，以建立可執行程式或動態連結程式庫。  
  
 編譯器會在遇到語法錯誤的轉譯階段發出警告或錯誤。  
  
 連結器會解析所有外部參考，並透過結合一個或多個分別處理的轉譯單位與標準程式庫建立可執行程式或 DLL。  
  
## <a name="see-also"></a>請參閱  
 [前置處理器](../preprocessor/preprocessor.md)