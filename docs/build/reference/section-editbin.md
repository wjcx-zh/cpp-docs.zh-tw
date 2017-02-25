---
title: "/SECTION (EDITBIN) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/section"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/SECTION editbin 選項"
  - "區段中的對齊字元"
  - "SECTION editbin 選項"
  - "-SECTION editbin 選項"
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /SECTION (EDITBIN)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/SECTION:name[=newname][,attributes][alignment]  
```  
  
## 備註  
 這個選項可變更區段的屬性 \(Attribute\)，覆寫在編譯或連結區段目的檔時所設定的屬性。  
  
 在冒號 \(**:**\) 後面，指定區段的名稱 \(*name*\)。  若要變更區段名稱，請在 *name* 後面接一個等號 \(\=\) 和區段的 *newname*。  
  
 若要設定或變更區段的屬性 `attributes`，請指定逗號 \(**,**\)，後面接一個或多個屬性字元。  若要取消屬性，請在屬性字元前面加一個驚嘆號 \(\!\)。  下列字元指定記憶體屬性：  
  
|屬性|設定|  
|--------|--------|  
|c|程式碼|  
|d|可捨棄|  
|e|executable|  
|i|初始化資料|  
|k|快取虛擬記憶體|  
|m|連結移除|  
|o|連結資訊|  
|p|分頁虛擬記憶體|  
|r|read|  
|s|shared|  
|u|未初始化資料|  
|w|write|  
  
 若要控制 *alignment*，請指定字元 **A**，後面接設定記憶體對齊大小的字元 \(以位元組為單位\)，如下所示：  
  
|字元|記憶體對齊大小 \(以位元組為單位\)|  
|--------|-------------------------|  
|1|1|  
|2|2|  
|4|4|  
|8|8|  
|p|16|  
|t|32|  
|s|64|  
|x|沒有對齊|  
  
 請以不含泛空白字元的字串指定 `attributes` 和 *alignment* 字元。  這些字元不區分大小寫。  
  
## 請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)