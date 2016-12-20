---
title: "SEGMENT | Microsoft Docs"
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
  - "SEGMENT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SEGMENT directive"
ms.assetid: e6f68367-6714-4f06-a79c-edfa88014430
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# SEGMENT
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

定義程式區段稱為*名稱*具有區段屬性  
  
## 語法  
  
```  
  
   name SEGMENT [[READONLY]] [[align]] [[combine]] [[use]] [[characteristics]] ALIAS(string) [['class']]  
statements  
name ENDS  
```  
  
#### 參數  
 *對齊*  
 可以從中選取段落的起始位址的記憶體位址範圍。  對齊型別可以是下列其中一項動作：  
  
|對齊類型|起始位址|  
|----------|----------|  
|**BYTE**|下一個可用的位元組的位址。|  
|**WORD**|下一個可用的 word 位址 \(每個字的 2 位元組\)。|  
|**DWORD**|下一個可用的雙字位址 \(每個雙字的 4 個位元組\)。|  
|**選取一個段落**|下一個可用的段落位址 \(每個段落的 16 位元組\)。|  
|**頁面**|下一個可用的網頁位址 \(每頁的 256 個位元組\)。|  
|**ALIGN**\(*n*\)|下一個可用 *n*第位元組的位址。  如需詳細資訊請參閱 ＜ 備註 ＞ 一節。|  
  
 如果未指定此參數， **段落**由預設值。  
  
 *結合*  
 **PUBLIC**, **STACK**, **COMMON**, **MEMORY**, **AT***address*, **PRIVATE**  
  
 *使用*  
 **USE16**, **USE32**, **FLAT**  
  
 `characteristics`  
 **INFO**, **READ**, **WRITE**, **EXECUTE**, **SHARED**, **NOPAGE**, **NOCACHE**, and **DISCARD**  
  
 這些都只支援 \(coff\)，並對應至 COFF 區段的特性相似的名稱 \(例如，  **SHARED** 會對應到 IMAGE\_SCN\_MEM\_SHARED\)。  讀取設定 IMAGE\_SCN\_MEM\_READ 旗標。  過時的唯讀旗標會導致清除 IMG\_SCN\_MEM\_WRITE 旗標的區段。  如果有任何`characteristics`設定，不會使用預設的特性，並只程式設計人員所指定的標幟才會生效。  
  
 `ALIAS(` `string` `)`  
 此字串用為發出 COFF 物件中的區段名稱。  建立具有相同的外部名稱，以不同的 MASM 區段名稱的多個節。  
  
 不支援以**\/omf**。  
  
 `class`  
 指定應該如何結合而排列組合的檔案中的區段。  Typical values are, `'DATA'`, `'CODE'`, `'CONST'` and`'STACK'`  
  
## 備註  
 For `ALIGN(``n``)`, `n` may be any power of 2 from 1 to 8192; 不支援**\/omf**。  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)