---
title: "遞迴函式 | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "函式呼叫, 遞迴"
  - "函式 [C], 遞迴呼叫"
  - "函式 [C], 遞迴"
  - "遞迴函式呼叫"
ms.assetid: 59739040-3081-4006-abbc-9d8423992bce
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 遞迴函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C 程式中的所有函式可以透過遞迴方式呼叫，即函式可以呼叫本身。  遞迴呼叫的數目受限於堆疊的大小。  如需設定堆疊大小的連結器選項詳細資訊，請參閱 [\/STACK \(堆疊配置\)](../build/reference/stack-stack-allocations.md) \(\/STACK\) 連結器選項。  每次呼叫函式就會為參數及 **auto** 和 **register** 變數配置新的儲存空間，以避免先前呼叫尚未完成的值被覆寫。  只有在建立參數的函數執行個體中才能直接存取這些參數。  之前的參數無法直接存取，以確保函式的執行個體。  
  
 請注意，具有 **static** 的變數宣告儲存不需要在每個遞迴呼叫中提供新的儲存空間。  其儲存空間會與程式的存留期同時存在。  對這類變數的每個參考都會存取相同的儲存區域。  
  
## 範例  
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
  
## 請參閱  
 [函式呼叫](../c-language/function-calls.md)