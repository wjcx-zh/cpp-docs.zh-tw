---
title: "語彙基元帶入的運算子 （#） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '##'
dev_langs: C++
helpviewer_keywords:
- preprocessor, operators
- '## preprocessor operator'
ms.assetid: 4f173503-990f-4bff-aef3-ec4d1f1458ef
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b2f77a2bd61080c398256c5d9c28085ec779d2e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="token-pasting-operator-"></a>語彙基元帶入的運算子 (##)
雙數字符號或 「 語彙基元帶入 」 運算子 (**##**)，有時稱為 「 合併 」 運算子，用於物件和函式類似巨集。 它可讓不同的語彙基元聯結成單一語彙基元，因此不可以是巨集定義中的第一個或最後一個語彙基元。  
  
 如果巨集定義中的開頭是型式參數，後方接著語彙基元帶入的運算子，則會立即以未展開的實際引數取代型式參數。 巨集展開會在引數取代之後才執行。  
  
 然後，語彙基元帶入運算子在每次發生*語彙基元字串*移除時，會串連前方及後方的語彙基元和。 產生的語彙基元必須是有效的語彙基元。 如果是的話，則會掃描語彙基元中是否存在代表巨集名稱的取代項目。 識別項會表示名稱，因此可在取代之前知悉程式中串連的語彙基元。 每一個語彙基元表示在其他位置定義 (可能是在程式或編譯器命令列中) 的語彙基元。 在運算子前方或後方的空白字元為選擇項。  
  
 這個範例示範如何在指定程式輸出時使用字串化和語彙基元帶入的運算子：  
  
```  
#define paster( n ) printf_s( "token" #n " = %d", token##n )  
int token9 = 9;  
```  
  
 如果使用如下的數值引數呼叫巨集  
  
```  
paster( 9 );  
```  
  
 巨集會產生  
  
```  
printf_s( "token" "9" " = %d", token9 );  
```  
  
 會變成  
  
```  
printf_s( "token9 = %d", token9 );  
```  
  
## <a name="example"></a>範例  
  
```  
// preprocessor_token_pasting.cpp  
#include <stdio.h>  
#define paster( n ) printf_s( "token" #n " = %d", token##n )  
int token9 = 9;  
  
int main()  
{  
   paster(9);  
}  
```  
  
```Output  
token9 = 9  
```  
  
## <a name="see-also"></a>請參閱  
 [前置處理器運算子](../preprocessor/preprocessor-operators.md)