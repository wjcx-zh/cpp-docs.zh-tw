---
title: "Safeintexception:: Safeintexception |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
dev_langs:
- C++
helpviewer_keywords:
- SafeIntException, constructor
ms.assetid: 8e5a0c24-a56b-4c80-9ee8-876604b1e7dc
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 85bf6bae5ba07154bdeb807171dd2d3df61d0774
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="safeintexceptionsafeintexception"></a>SafeIntException::SafeIntException
建立 `SafeIntException` 物件。  
  
## <a name="syntax"></a>語法  
  
```  
SafeIntException();  
  
SafeIntException(  
   SafeIntError code  
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `code`  
 描述發生之錯誤的列舉的資料值。  
  
## <a name="remarks"></a>備註  
 可能值`code`Safeint.h 檔案中所定義。 為了方便起見，可能的值也會列出以下。  
  
-   `SafeIntNoError`  
  
-   `SafeIntArithmeticOverflow`  
  
-   `SafeIntDivideByZero`  
  
## <a name="requirements"></a>需求  
 **標頭：** safeint.h  
  
 **命名空間：** msl::utilities  
  
## <a name="see-also"></a>請參閱  
 [SafeInt 程式庫](../windows/safeint-library.md)   
 [SafeIntException 類別](../windows/safeintexception-class.md)   
 [SafeInt 類別](../windows/safeint-class.md)