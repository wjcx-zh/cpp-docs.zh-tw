---
title: "結構的儲存和對齊 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "結構的對齊"
  - "封裝結構"
  - "儲存結構"
  - "結構儲存"
ms.assetid: 60ff292f-2595-4f37-ae00-4c4b4f047196
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 結構的儲存和對齊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 結構成員會依其宣告的順序依序儲存：第一個成員具有最低的記憶體位址，最後一個成員則具有最高的記憶體位址。  
  
 每個資料物件都有一個 *alignment\-requirement*。  如果是結構，這個要求是其最大的成員。  每個物件都會配置一個 *offset*，因此  
  
 *offset* `%` *alignment\-requirement* `==` 0  
  
 如果整數類資料類型的大小相同，而且下一個位元欄位符合目前配置單位，不需因為位元欄位的一般對齊需求而加上跨越界限，則相鄰的位元欄位會封裝為相同的 1 個、2 個或 4 個位元組配置單位。  
  
 若要保留空間或符合現有的資料結構，您可能想要或多或少精簡地儲存結構。  [\/Zp](../build/reference/zp-struct-member-alignment.md)\[*n*\] 編譯器選項和 [\#pragma pack](../preprocessor/pack.md) 可控制將結構資料「封裝」至記憶體的方式。  當您使用 \/Zp \[*n*\] 選項 \(其中 *n* 為 1、2、4、8 或 16\) 時，第一個結構成員之後的每個結構成員會儲存在位元組界限上，可能是欄位或封裝大小 \(*n*\) 的對齊需求，取兩者中較小者。  表示為公式，位元組界限為  
  
```  
min( n, sizeof( item ) )  
```  
  
 其中 *n* 是封裝大小，以 \/Zp \[*n*\] 選項表示，而 *item* 為結構成員。  預設的封裝大小是 \/Zp8。  
  
 若要使用 `pack` pragma 來指定封裝 \(在命令列上為特定結構指定的封裝除了\)，請在結構的前方使用 `pack` pragma，其中封裝大小為 1、2、4、8 或 16。  若要重新啟用在命令列上指定的封裝，請指定沒有引數的 `pack` pragma。  
  
 Microsoft C 編譯器的位元欄位預設大小為 **long**。  結構成員會對齊於類型的大小或 \/Zp \[*n*\] 的大小，取兩者中較小者。  預設大小為 4。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [結構宣告](../c-language/structure-declarations.md)