---
title: lock 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::lock
- msclr.lock
- lock
dev_langs:
- C++
helpviewer_keywords:
- lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a860f79b740e0f34eef33b7a96e0236835f1f6b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="lock-class"></a>lock 類別
這個類別會自動進行同步處理從多個執行緒存取物件的鎖定。  當建構它取得的鎖定和終結該版本時鎖定。  
  
## <a name="syntax"></a>語法  
  
```  
ref class lock;  
```  
  
## <a name="remarks"></a>備註  
 `lock` 僅適用於 CLR 物件，只用於 CLR 程式碼中。  
  
 就內部而言，鎖定類別會使用<xref:System.Threading.Monitor>以同步存取。 在同步處理，請參閱這個主題更詳細的資訊。  
  
## <a name="requirements"></a>需求  
 **標頭檔** \<msclr\lock.h >  
  
 **命名空間**msclr  
  
## <a name="see-also"></a>另請參閱  
 [lock](../dotnet/lock.md)   
 [lock 成員](../dotnet/lock-members.md)