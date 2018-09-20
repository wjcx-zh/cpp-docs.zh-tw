---
title: no_registry |Microsoft Docs
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
ms.openlocfilehash: 8071fdf5e18542273dddfacecca913130e7bdea6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381227"
---
# <a name="noregistry"></a>no_registry
**no_registry**會告知編譯器不要搜尋類型程式庫匯入登錄`#import`。  
  
## <a name="syntax"></a>語法  
  
```  
#import filename no_registry  
```  
  
### <a name="parameters"></a>參數  
*filename*  
類型程式庫。  
  
## <a name="remarks"></a>備註  
 
如果在 include 目錄中找不到參考的型別程式庫，編譯將會失敗，即使是在登錄中的型別程式庫。  **no_registry**隱含匯入與其他型別程式庫會傳播`auto_search`。  
  
編譯器永遠不會搜尋以檔案名稱指定並直接傳遞至 `#import` 之類別程式庫的登錄。  
  
當`auto_search`指定，則額外`#import`s 會產生含有**no_registry**的初始設定`#import`(如果初始`#import`指示詞**no_registry**，則`auto_search`-產生`#import`還有**no_registry**。)  
  
**no_registry**如果您想要匯入交互參考的型別程式庫，而不會在登錄中尋找檔案的較舊版本的編譯器會很有用。 **no_registry**也很有用，如果尚未註冊類型程式庫。  
  
## <a name="see-also"></a>另請參閱  
 
[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)