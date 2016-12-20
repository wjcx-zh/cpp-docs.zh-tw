---
title: "二元運算子 | Microsoft Docs"
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
  - "二元運算子"
  - "成員選取運算子"
  - "運算子 [C++], 二進位"
ms.assetid: c0e7fbff-bc87-4708-8333-504ac09ee83e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 二元運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表顯示可以多載的運算子清單。  
  
### 可重新定義的二元運算子  
  
|運算子|名稱|  
|---------|--------|  
|**,**|逗號|  
|`!=`|不等|  
|`%`|模數|  
|`%=`|模數\/指派|  
|**&**|位元 AND|  
|**&&**|邏輯 AND|  
|**&\=**|位元 AND\/指派|  
|**\***|乘法|  
|**\*\=**|乘法\/指派|  
|**\+**|加入|  
|`+=`|加法\/指派|  
|**–**|減法|  
|**–\=**|減法\/指派|  
|**–\>**|成員選取|  
|**–\>\***|成員指標選取|  
|**\/**|除法|  
|`/=`|除法\/指派|  
|**\<**|小於|  
|**\<\<**|左移|  
|**\<\<\=**|左移\/指派|  
|**\<\=**|小於或等於|  
|**\=**|指派|  
|`==`|相等|  
|**\>**|大於|  
|**\>\=**|大於或等於|  
|**\>\>**|右移|  
|**\>\>\=**|右移\/指派|  
|**^**|互斥 OR|  
|`^=`|互斥 OR\/指派|  
|**&#124;**|位元包含 OR|  
|`&#124;=`|位元包含 OR\/指派|  
|`&#124;&#124;`|邏輯 OR|  
  
 若要將二元運算子函式宣告為非靜態成員，您必須以此格式進行宣告：  
  
 *ret\-type* **operator**`op`**\(** `arg` **\)**  
  
 其中 *ret\-type*為傳回類型，`op` 是上表中所列的其中一個運算子，而 `arg` 是任何類型的引數。  
  
 若要將二元運算子函式宣告為全域函式，您必須以此格式進行宣告：  
  
 *ret\-type* **operator**`op`**\(** `arg1`**,** `arg2` **\)**  
  
 其中 *ret\-type* 和 `op` 是成員運算子函式，而 `arg1` 和 `arg2` 是引數。  至少要有一個引數是類別類型。  
  
> [!NOTE]
>  二元運算子的傳回類型不受限制；不過，大部分使用者定義的二元運算子會傳回類別類型或類別類型的參考。  
  
## 請參閱  
 [運算子多載](../cpp/operator-overloading.md)