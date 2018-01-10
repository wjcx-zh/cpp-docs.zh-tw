---
title: "複合陳述式 (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- compound statements
- statements, compound
ms.assetid: 32d1bf86-cbbc-42a9-ba3a-1be1c6c7754c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9422e3229aa5e800859f50e1ca058e32a4120074
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compound-statement-c"></a>複合陳述式 (C)
複合陳述式 (也稱為「區塊」) 通常會以另一個陳述式主體的形式出現，例如 **if** 陳述式。 [宣告和類型](../c-language/declarations-and-types.md)會描述可能出現在複合陳述式開頭的宣告形式和意義。  
  
## <a name="syntax"></a>語法  
 *compound-statement*:  
 **{**  *declaration-list* opt*statement-list*opt**}**  
  
 *declaration-list*:  
 *declaration*  
  
 *declaration-list declaration*  
  
 *statement-list*:  
 s*tatement*  
  
 *statement-list statement*  
  
 如果出現宣告，則必須位於任何陳述式前面。 在複合陳述式開頭宣告之每個識別項的範圍，都會從其宣告點延伸至區塊結尾。 除非內部區塊中存在相同識別項的宣告，否則都可在整個區塊中看見此範圍。  
  
 除非以 **register**、**static** 或 `extern` 另外明確宣告，否則複合陳述式中的識別項會假設為 **auto**，但函式除外，函式只能是 `extern`。 您可以在函式宣告中省略 `extern` 規範，且函式仍會是 `extern`。  
  
 如果變數或函式在複合陳述式中是以儲存類別 `extern` 宣告，則不會配置儲存，且不允許初始化。 宣告會參考其他位置所定義的外部變數或函式。  
  
 在區塊中以 **auto** 或 **register** 關鍵字宣告的變數會重新配置，而且如有需要，會在每次進入複合陳述式時初始化。 這些變數不是在複合陳述式結束之後定義。 如果區塊內宣告的變數擁有 **static** 屬性，則變數會在程式開始執行時初始化，並且在程式執行過程中保留其值。 如需有關 **static** 的詳細資訊，請參閱[儲存類別](../c-language/c-storage-classes.md)。  
  
 這個範例將示範複合陳述式：  
  
```  
if ( i > 0 )   
{  
    line[i] = x;  
    x++;  
    i--;  
}  
```  
  
 在這個範例中，如果 `i` 大於 0，則複合陳述式內的所有陳述式會依序執行。  
  
## <a name="see-also"></a>請參閱  
 [陳述式](../c-language/statements-c.md)