---
title: "implementation_only |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implementation_only
dev_langs:
- C++
helpviewer_keywords:
- implementation_only attribute
ms.assetid: d8cabc86-4425-45a0-9587-d57536980088
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aa9fe0e8bf3cdecbdf118219cfe91be03a85a51f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="implementationonly"></a>implementation_only
**C + + 特定的**  
  
 不產生 .tlh 標頭檔 (主要標頭檔)。  
  
## <a name="syntax"></a>語法  
  
```  
implementation_only  
```  
  
## <a name="remarks"></a>備註  
 這個檔案包含所有用於公開類型程式庫內容的宣告。 實作包裝函式成員函式時，會產生 .tli 標頭檔並包含在編譯中。  
  
 指定這個屬性時，.tli 標頭的內容會在 .tlh 標頭通常使用的相同命名空間中。 此外，不會將成員函式宣告為內嵌。  
  
 `implementation_only`屬性僅供搭配使用[no_implementation](../preprocessor/no-implementation.md)屬性當做方式，來保留從先行編譯標頭 (PCH) 檔案的實作。 具有 `#import` 屬性的 `no_implementation` 陳述式是置於用來建立 PCH 的來源範圍中。 產生的 PCH 會供許多原始程式檔使用。 然後具有 `#import` 屬性的 `implementation_only` 陳述式會在 PCH 範圍以外使用。 您只能在其中一個原始程式檔中使用此陳述式一次。 如此會產生所有必要的包裝函式成員函式，而不需要額外重新編譯每個原始程式檔。  
  
> [!NOTE]
>  `implementation_only` 陳述式中的 `#import` 屬性必須與另一個 `#import` 陳述式搭配使用，而該陳述式屬於同一個類型程式庫且具有 `no_implementation` 屬性。 否則，就會產生編譯器錯誤。 這是因為必須要有具 `#import` 屬性的 `no_implementation` 陳述式所產生的包裝函式類別定義，才能編譯 `implementation_only` 屬性所產生的實作。  
  
 **END c + + 特定的**  
  
## <a name="see-also"></a>請參閱  
 [#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指示詞](../preprocessor/hash-import-directive-cpp.md)