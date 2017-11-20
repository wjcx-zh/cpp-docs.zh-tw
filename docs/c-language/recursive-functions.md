---
title: "遞迴函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- functions [C], recursive
- function calls, recursive
- functions [C], calling recursively
- recursive function calls
ms.assetid: 59739040-3081-4006-abbc-9d8423992bce
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cca28b41b15ae14504ac5692a3e8a7063a11e862
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="recursive-functions"></a>遞迴函式
C 程式中的所有函式可以透過遞迴方式呼叫，即函式可以呼叫本身。 遞迴呼叫的數目受限於堆疊的大小。 如需設定堆疊大小的連結器選項相關資訊，請參閱 [/STACK (堆疊配置)](../build/reference/stack-stack-allocations.md) (/STACK) 連結器選項。 每次呼叫函式就會為參數及 **auto** 和 **register** 變數配置新的儲存空間，以避免覆寫先前尚未完成呼叫的值。 只有在建立參數的函數執行個體中才能直接存取這些參數。 之前的參數無法直接存取，以確保函式的執行個體。  
  
 請注意，以 **static** 儲存空間宣告的變數，在每次遞迴呼叫時不需要新的儲存空間。 其儲存空間會與程式的存留期同時存在。 對這類變數的每個參考都會存取相同的儲存區域。  
  
## <a name="example"></a>範例  
 下列範例示範遞迴呼叫：  
  
```  
int factorial( int num );      /* Function prototype */  
  
int main()  
{  
    int result, number;  
    .  
    .  
    .  
    result = factorial( number );  
}  
  
int factorial( int num )      /* Function definition */  
{  
    .  
    .  
    .  
    if ( ( num > 0 ) || ( num <= 10 ) )  
        return( num * factorial( num - 1 ) );  
}  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [函式呼叫](../c-language/function-calls.md)