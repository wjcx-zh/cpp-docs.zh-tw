---
title: "CString Semantics | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "指派陳述式, assigning CString objects"
  - "CString objects, assignment semantics"
  - "semantics in Cstring"
ms.assetid: d4023480-526f-499a-85f6-324b4de5b85f
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CString Semantics
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

即使 [CString](../atl-mfc-shared/reference/cstringt-class.md) 物件是可擴充的動態物件，其運作方式與內建基本型別和簡單的類別。  每個 `CString` 物件表示唯一值。  您應該將 \[`CString` 物件做為實際資料而不是指向字串。  
  
 您可以將 **CString** 物件與另一個。  不過，在中，當您修改這兩個 `CString` 物件的其中一個時，另一個 `CString` 物件不會被修改，如下列範例所示:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#188](../atl-mfc-shared/codesnippet/CPP/cstring-semantics_1.cpp)]  
  
 在範例中的注意事項 `CString` 兩個物件視為「等於」，因為它們表示相同的字串。  `CString` 類別會多載等號比較運算子 \(`==`\) 會根據其值的兩個 `CString` 物件 \(內容\) 而不是其識別 \(位址\)。  
  
## 請參閱  
 [字串](../atl-mfc-shared/strings-atl-mfc.md)