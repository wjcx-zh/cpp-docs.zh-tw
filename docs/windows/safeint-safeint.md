---
title: "Safeint:: Safeint |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SafeInt::SafeInt
- SafeInt
- SafeInt.SafeInt
dev_langs:
- C++
helpviewer_keywords:
- SafeInt class, constructor
ms.assetid: 39e6f632-a396-40e6-9ece-cc3d4c5a78ef
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a9820227384866cdb1a6470ebd9650187848334c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="safeintsafeint"></a>SafeInt::SafeInt
建構 `SafeInt` 物件。  
  
## <a name="syntax"></a>語法  
  
```  
SafeInt() throw  
  
SafeInt (  
   const T& i  
) throw ()  
  
SafeInt (  
   bool b  
) throw ()  
  
template <typename U>  
SafeInt (  
   const SafeInt <U, E>& u  
)  
  
I template <typename U>  
SafeInt (  
   const U& i  
)  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `i`  
 新的值`SafeInt`物件。 這必須是類型 T 或 U，根據建構函式的參數。  
  
 [輸入] `b`  
 新的布林值`SafeInt`物件。  
  
 [輸入] `u`  
 A`SafeInt`為類型 u。新`SafeInt`物件會具有相同的值做為`u`，但會為類型 t。  
  
 U  
 中儲存的資料型別`SafeInt`。 這可以是布林值、 字元或整數類型。 如果是整數類型，它可以是帶正負號或不帶正負號和介於 8 到 64 位元。  
  
## <a name="remarks"></a>備註  
 如需有關範本類型`T`和`E`，請參閱[SafeInt 類別](../windows/safeint-class.md)。  
  
 輸入的參數的建構函式，`i`或`u`，必須是布林值、 字元或整數類型。 如果它是另一個類型的參數，`SafeInt`類別會呼叫[static_assert](../cpp/static-assert.md)表示無效的輸入的參數。  
  
 使用範本類型的建構函式`U`自動轉換為所指定之類型的 輸入的參數`T`。 `SafeInt`類別會轉換成沒有遺失任何資料的資料。 它會報告錯誤處理常式`E`如果它無法轉換輸入資料`T`不會遺失資料。  
  
 如果您建立`SafeInt`從布林值參數，您需要立即初始化值。 無法建構`SafeInt`使用程式碼`SafeInt<bool> sb;`。 這會產生編譯錯誤。  
  
## <a name="requirements"></a>需求  
 **標頭：** safeint.h  
  
 **命名空間：** msl::utilities  
  
## <a name="see-also"></a>請參閱  
 [SafeInt 程式庫](../windows/safeint-library.md)   
 [SafeInt 類別](../windows/safeint-class.md)   
 [SafeIntException 類別](../windows/safeintexception-class.md)