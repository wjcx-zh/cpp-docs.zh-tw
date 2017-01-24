---
title: "使用 dllexport 和 dllimport 定義內嵌 C++ 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "dllexport 屬性 [C++], 內嵌函式"
  - "dllimport 屬性 [C++], 內嵌函式"
  - "函式 [C++], 定義內嵌"
  - "內嵌函式 [C++], 定義"
ms.assetid: 3b48678b-e7b8-4eda-bb46-b5d34dcf7817
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 dllexport 和 dllimport 定義內嵌 C++ 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 您可以將具有 `dllexport` 屬性的函式定義為內嵌。  在這種情況下，無論程式中是否有任何模組參考函式，函式都一定會具現化並匯出。  函式會假定為由其他程式匯入。  
  
 您也可以將使用 **dllimport** 屬性宣告的函式定義為內嵌。  在這種情況下，函式可以展開 \(須遵循 \/Ob 規格\)，但絕不會具現化。  特別是，如果接受匯入的內嵌函式位址，則會傳回位於 DLL 中函式的位址。  這種行為與接受匯入的非內嵌函式位址相同。  
  
 這些規則適用於其定義出現在類別定義內的內嵌函式。  此外，內嵌函式中的靜態區域資料和字串會在 DLL 和用戶端之間維護相同的識別，就像在單一程式 \(也就是沒有 DLL 介面的可執行檔\) 中一樣。  
  
 提供匯入的內嵌函式時務必特別小心。  例如，如果您更新 DLL，請不要假設用戶端將會使用變更後的 DLL 版本。  若要確保載入正確的 DLL 版本，請一併重建 DLL 的用戶端。  
  
## END Microsoft 特定的  
  
## 請參閱  
 [dllexport、dllimport](../cpp/dllexport-dllimport.md)