---
title: "類型程式庫存取 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- type libraries, accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 8a3fbcf66036ef3df3bd34b5182dac8af3dfccef
ms.lasthandoff: 02/24/2017

---
# <a name="type-library-access"></a>類型程式庫存取
類型程式庫會將 OLE 控制項的介面公開給其他 OLE 感知應用程式。 如果有一個或多個介面要公開，則每個 OLE 控制項都必須有類型程式庫。  
  
 下列巨集可以讓 OLE 控制項提供對其類型程式庫的存取能力：  
  
### <a name="type-library-access"></a>類型程式庫存取  
  
|||  
|-|-|  
|[DECLARE_OLETYPELIB](#declare_oletypelib)|宣告 OLE 控制項的 `GetTypeLib` 成員函式 (必須在類別宣告中使用)。|  
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|實作 OLE 控制項的 `GetTypeLib` 成員函式 (必須在類別實作中使用)。|  
  
##  <a name="a-namedeclareoletypeliba--declareoletypelib"></a><a name="declare_oletypelib"></a>DECLARE_OLETYPELIB  
 宣告`GetTypeLib`控制類別成員函式。  
  
```   
DECLARE_OLETYPELIB(class_name)   
```  
  
### <a name="parameters"></a>參數  
 *class_name*  
 控制項類別相關的類型程式庫的名稱。  
  
### <a name="remarks"></a>備註  
 控制項類別標頭檔中使用這個巨集。  

### <a name="requirements"></a>需求  
 **標頭：** afxdisp.h  

##  <a name="a-nameimplementoletypeliba--implementoletypelib"></a><a name="implement_oletypelib"></a>IMPLEMENT_OLETYPELIB  
 實作控制項的`GetTypeLib`成員函式。  
  
```   
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)   
```  
  
### <a name="parameters"></a>參數  
 *class_name*  
 控制項類別相關的類型程式庫的名稱。  
  
 *tlid*  
 型別程式庫 ID 編號。  
  
 `wVerMajor`  
 類型程式庫主要版本號碼。  
  
 `wVerMinor`  
 類型程式庫次要版本號碼。  
  
### <a name="remarks"></a>備註  
 這個巨集必須出現在使用任何控制項類別的實作檔`DECLARE_OLETYPELIB`巨集。  

### <a name="requirements"></a>需求  
 **標頭：** afxdisp.h  
   
## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)

