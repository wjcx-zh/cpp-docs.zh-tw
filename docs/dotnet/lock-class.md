---
title: "lock 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- msclr::lock
- msclr.lock
- lock
dev_langs: C++
helpviewer_keywords: lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c2f2a8e371803d33a2c42508ec595681ada3bab8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="lock-class"></a>lock 類別
這個類別會自動進行同步處理從多個執行緒存取物件的鎖定。  當建構它取得的鎖定和終結該版本時鎖定。  
  
## <a name="syntax"></a>語法  
  
```  
ref class lock;  
```  
  
## <a name="remarks"></a>備註  
 `lock`僅適用於 CLR 物件，只用於 CLR 程式碼中。  
  
 就內部而言，鎖定類別會使用<xref:System.Threading.Monitor>以同步存取。 在同步處理，請參閱這個主題更詳細的資訊。  
  
## <a name="requirements"></a>需求  
 **標頭檔** \<msclr\lock.h >  
  
 **命名空間**msclr  
  
## <a name="see-also"></a>請參閱  
 [鎖定](../dotnet/lock.md)   
 [lock 成員](../dotnet/lock-members.md)