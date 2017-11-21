---
title: "Platform:: arrayreference 類別 |Microsoft 文件"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VCCORLIB/Platform::ArrayReference::ArrayReference
dev_langs: C++
helpviewer_keywords: Platform::ArrayReference Class
ms.assetid: 9ab3b15e-8a60-4600-8fcb-7d6c86284f4b
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: d2de3a679f4abd70dfeda04cd0ea8a2ebcd3b4c6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="platformarrayreference-class"></a>Platform::ArrayReference 類別
`ArrayReference` 是最佳化類型，當您想要使用輸入資料填入 C-style 陣列時，可以使用它來替代輸入參數中的 [Platform::Array^](../cppcx/platform-array-class.md) 。  
  
## <a name="syntax"></a>語法  
  
```cpp  
class ArrayReference  
```
  
### <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[Arrayreference:: Arrayreference](#ctor)|初始化 `ArrayReference` 類別的新執行個體。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[ArrayReference::operator() 運算子](#operator-call)|將這個 `ArrayReference` 轉換成 `Platform::Array<T>^*`。|  
|[ArrayReference::operator= 運算子](#operator-assign)|將另一個 `ArrayReference` 的內容指派給這個執行個體。|  
  
## <a name="exceptions"></a>例外狀況  
  
### <a name="remarks"></a>備註  
 使用 `ArrayReference` 填滿 C-style 陣列時，可避免先複製到 `Platform::Array` 變數然後複製到 C-style 陣列時所牽涉到的額外複製作業。 當您使用 `ArrayReference`時，只會有一項複製作業。 如需程式碼範例，請參閱[Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。  
  
### <a name="requirements"></a>需求  
 **最低支援用戶端：** Windows 8  
  
 **最低支援伺服器：** Windows Server 2012  
  
 **命名空間：** Platform  
  
 **標頭：** vccorlib.h  
  
## <a name="ctor"></a>Arrayreference:: Arrayreference 建構函式
初始化的新執行個體[platform:: arrayreference](../cppcx/platform-arrayreference-class.md)類別。  
  
### <a name="syntax"></a>語法  
  
```cpp  
ArrayReference(TArg* ataArg, unsigned int sizeArg, bool needsInitArg = false);  
ArrayReference(ArrayReference&& otherArg)  
  
```  
  
### <a name="parameters"></a>參數  
 `dataArg`  
 陣列資料的指標。  
  
 `sizeArg`  
 來源陣列中的元素數目。  
  
 `otherArg`  
 將會移動其資料來初始化新執行個體的 `ArrayReference` 物件。  
  
### <a name="remarks"></a>備註  
  


## <a name="operator-assign"></a>Arrayreference:: Operator = 運算子
將指定的物件指派給目前[platform:: arrayreference](../cppcx/platform-arrayreference-class.md)使用移動語意的物件。  
  
### <a name="syntax"></a>語法  
  
```cpp  
  
ArrayReference& operator=(ArrayReference&& otherArg);  
  
```  
  
### <a name="parameters"></a>參數  
 `otherArg`  
 移至目前 `ArrayReference` 物件的物件。  
  
### <a name="return-value"></a>傳回值  
 類型為 `ArrayReference` 之物件的參考。  
  
### <a name="remarks"></a>備註  
 `Platform::ArrayReference` 是標準 C++ 類別樣板，而不是 ref 類別。  
  


## <a name="operator-call"></a>Arrayreference 運算子
將目前[platform:: arrayreference](../cppcx/platform-arrayreference-class.md)回物件[platform:: array](../cppcx/platform-array-class.md)類別。  
  
### <a name="syntax"></a>語法  
  
```cpp  
  
Array<TArg>^ operator ();  
  
```  
  
### <a name="return-value"></a>傳回值  
 `Array<TArg>^` 類型之物件的控制代碼  
  
### <a name="remarks"></a>備註  
 [Platform:: arrayreference](../cppcx/platform-arrayreference-class.md)和[platform:: array](../cppcx/platform-array-class.md)是標準 c + + 類別樣板，而不是 ref 類別。  
  


  
  
## <a name="see-also"></a>另請參閱  
 [Platform 命名空間](../cppcx/platform-namespace-c-cx.md)