---
title: "運算式的摘要 | Microsoft Docs"
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
ms.assetid: ed448953-687a-4b57-a1cb-12967bd770ea
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 運算式的摘要
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*primary\-expression*：  
 *識別項*  
  
 *常數*  
  
 *字串常值*  
  
 **\(**  *expression*  **\)**  
  
 *expression*：  
 *assignment\-expression*  
  
 *expression*  **,**  *assignment\-expression*  
  
 *constant\-expression*:  
 *條件運算式*  
  
 *conditional\-expression*:  
 *logical\-OR\-expression*  
  
 *logical\-OR\-expression*  **?**  *expression*  **:**  *conditional\-expression*  
  
 *assignment\-expression*：  
 *條件運算式*  
  
 *一元運算式指派運算子指派運算式*  
  
 *postfix\-expression*：  
 *primary\-expression*  
  
 *postfix\-expression*  **\[**  *expression*  **\]**  
  
 *postfix\-expression*  **\(**  *argument\-expression\-list*  opt **\)**  
  
 *postfix\-expression*  **.**  *identifier*  
  
 *postfix\-expression*  **–\>**  *identifier*  
  
 *postfix\-expression*  **\+\+**  
  
 *postfix\-expression*  **––**  
  
 *argument\-expression\-list*：  
 *assignment\-expression*  
  
 *argument\-expression\-list*  **,**  *assignment\-expression*  
  
 *unary\-expression*：  
 *postfix\-expression*  
  
 **\+\+**  *unary\-expression*  
  
 **––**  *unary\-expression*  
  
 *unary\-operator*  
  
 *cast\-expression*  
  
 **sizeof**  *unary\-expression*  
  
 **sizeof \(**  *type\-name*  **\)**  
  
 *unary\-operator*：下列其中一項  
 **& \* \+ – ~ \!**  
  
 *cast\-expression*：  
 *unary\-expression*  
  
 **\(**  *type\-name*  **\)**  *cast\-expression*  
  
 *multiplicative\-expression*：  
 *cast\-expression*  
  
 *multiplicative\-expression*  **\***  *cast\-expression*  
  
 *multiplicative\-expression*  **\/**  *cast\-expression*  
  
 *multiplicative\-expression*  **%**  *cast\-expression*  
  
 *additive\-expression*：  
 *multiplicative\-expression*  
  
 *additive\-expression*  **\+**  *multiplicative\-expression*  
  
 *additive\-expression*  **–**  *multiplicative\-expression*  
  
 *shift\-expression*:  
 *additive\-expression*  
  
 *shift\-expression*  **\<\<**  *additive\-expression*  
  
 *shift\-expression*  **\>\>**  *additive\-expression*  
  
 *relational\-expression*:  
 *shift\-expression*  
  
 *relational\-expression*  **\<**  *shift\-expression*  
  
 *relational\-expression*  **\>**  *shift\-expression relational\-expression*  **\<\=**  *shift\-expression*  
  
 *relational\-expression*  **\>\=**  *shift\-expression*  
  
 *equality\-expression*:  
 *relational\-expression*  
  
 *equality\-expression*  **\=\=**  *relational\-expression*  
  
 *equality\-expression*  **\!\=**  *relational\-expression*  
  
 *AND\-expression*：  
 *equality\-expression*  
  
 *AND\-expression*  **&**  *equality\-expression*  
  
 *exclusive\-OR\-expression*：  
 *AND\-expression*  
  
 *exclusive\-OR\-expression*  **^**  *AND\-expression*  
  
 *inclusive\-OR\-expression*：  
 *exclusive\-OR\-expression*  
  
 *inclusive\-OR\-expression* **&#124;**   *exclusive\-OR\-expression*  
  
 *logical\-AND\-expression*：  
 *inclusive\-OR\-expression*  
  
 *logical\-AND\-expression*  **&&**  *inclusive\-OR\-expression*  
  
 *logical\-OR\-expression*：  
 *logical\-AND\-expression*  
  
 *logical\-OR\-expression*  **&#124;&#124;**  *logical\-AND\-expression*  
  
## 請參閱  
 [階段結構文法](../c-language/phrase-structure-grammar.md)