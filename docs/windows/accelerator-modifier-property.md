---
title: "快速鍵輔助按鍵屬性 | Microsoft Docs"
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
  - "Modifier 屬性"
ms.assetid: f05a9379-e037-4cfb-b6ef-d2c655bcfa7f
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 快速鍵輔助按鍵屬性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表列出快速鍵 \(Accelerator\) 對應表中輔助按鍵屬性的合法項目。  
  
|值|描述|  
|-------|--------|  
|**None**|使用者只按下按鍵值。  這最常用於 001 到 026 的 ASCII\/ANSI 值，它們分別解譯為 ^A 到 ^Z \(CTRL\-A 到 CTRL\-Z\)。|  
|**ALT**|使用者必須在按下按鍵值之前先按下 ALT 鍵。|  
|**Ctrl**|使用者必須在按下按鍵值之前先按下 CTRL 鍵。  不適用於 ASCII 類型。|  
|**Shift**|使用者必須在按下按鍵值之前先按下 SHIFT 鍵。|  
|**CTRL\+ALT**|使用者必須在按下按鍵值之前先按下 CTRL 鍵和 ALT 鍵。  不適用於 ASCII 類型。|  
|**CTRL\+SHIFT**|使用者必須在按下按鍵值之前先按下 CTRL 鍵和 SHIFT 鍵。  不適用於 ASCII 類型。|  
|**ALT\+SHIFT**|使用者必須在按下按鍵值之前先按下 ALT 鍵和 SHIFT 鍵。  不適用於 ASCII 類型。|  
|**CTRL\+ALT\+SHIFT**|使用者必須在按下按鍵值之前先按下 CTRL、ALT 和 SHIFT 鍵。  不適用於 ASCII 類型。|  
  
## 需求  
 Win32  
  
## 請參閱  
 [Setting Accelerator Properties](../windows/setting-accelerator-properties.md)   
 [Accelerator Editor](../mfc/accelerator-editor.md)