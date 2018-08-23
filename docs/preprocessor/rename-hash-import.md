---
title: 重新命名 (#import) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Rename
dev_langs:
- C++
helpviewer_keywords:
- rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2930ab9cbc5b847252e20f185b335a547317fa5b
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2018
ms.locfileid: "42539761"
---
# <a name="rename-import"></a>rename (#import)
**C + + 特定**  
  
解決名稱衝突問題。  
  
## <a name="syntax"></a>語法  
  
```  
rename("OldName","NewName")  
```  
  
### <a name="parameters"></a>參數  
*OldName*  
類型程式庫中的舊名稱。  
  
*NewName*  
用來取代舊名稱的名稱。  
  
## <a name="remarks"></a>備註  
 
如果指定此屬性，則編譯器會取代所有出現*OldName*中的使用者提供的型別程式庫*NewName*產生的標頭檔中。  
  
當類型程式庫中的名稱與系統標頭檔中的巨集定義相符時，才能使用這個屬性。 如果未解決這種情況，則多個語法錯誤，將會產生這類[編譯器錯誤 C2059](../error-messages/compiler-errors-1/compiler-error-c2059.md)並[編譯器錯誤 C2061](../error-messages/compiler-errors-1/compiler-error-c2061.md)。  
  
> [!NOTE]
> 取代適用於類型程式庫中使用的名稱，不適用於所產生標頭檔中使用的名稱。  
  
例如，假設屬性名稱 `MyParent` 存在於類型程式庫中，而標頭檔中已定義巨集 `GetMyParent`，且已在 `#import` 之前使用。 由於`GetMyParent`是一個包裝函式的預設名稱，來處理錯誤`get`屬性，就會發生名稱衝突。 若要解決此問題，請在 `#import` 陳述式中使用下列屬性：  
  
```  
rename("MyParent","MyParentX")  
```  
  
其中會重新命名類型程式庫中的名稱 `MyParent`。 嘗試重新命名 `GetMyParent` 包裝函式名稱將會失敗：  
  
```  
rename("GetMyParent","GetMyParentX")  
```  
  
這是因為名稱 `GetMyParent` 只會出現在產生的類型程式庫標頭檔中。  
  
**END c + + 特定的**  
  
## <a name="see-also"></a>另請參閱  
 
[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)