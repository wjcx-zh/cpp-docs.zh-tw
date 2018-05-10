---
title: no_registry |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_registry
dev_langs:
- C++
helpviewer_keywords:
- no_registry attribute
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 416663592f4362c110637fb4d4b4b418d9776cde
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="noregistry"></a>no_registry
`no_registry` 會告知編譯器不要搜尋以 `#import` 匯入之類型程式庫的登錄。  
  
## <a name="syntax"></a>語法  
  
```  
  
#import filename no_registry  
```  
  
#### <a name="parameters"></a>參數  
 *filename*  
 類型程式庫。  
  
## <a name="remarks"></a>備註  
 如果 include 目錄中找不到參考的型別程式庫，編譯會失敗，即使是在登錄中的型別程式庫。  `no_registry` 會傳播至隱含地匯入與其他類型程式庫`auto_search`。  
  
 編譯器永遠不會搜尋以檔案名稱指定並直接傳遞至 `#import` 之類別程式庫的登錄。  
  
 指定 `auto_search` 時，會產生其他 `#import` 且包含初始 `no_registry` 的 `#import` 設定 (如果最初的 `#import` 指示詞是 `no_registry`，`auto_search` 產生的 `#import` 也是 `no_registry`)。  
  
 `no_registry` 如果您想要匯入交互參考的類型程式庫，而不會在登錄中尋找檔案的較舊版本的編譯器，相當實用。  `no_registry` 也很有用，如果尚未註冊類型程式庫。  
  
## <a name="see-also"></a>另請參閱  
 [#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指示詞](../preprocessor/hash-import-directive-cpp.md)