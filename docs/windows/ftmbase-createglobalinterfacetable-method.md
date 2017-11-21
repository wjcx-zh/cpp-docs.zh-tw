---
title: "Ftmbase:: Createglobalinterfacetable 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: ftm/Microsoft::WRL::FtmBase::CreateGlobalInterfaceTable
dev_langs: C++
helpviewer_keywords: CreateGlobalInterfaceTable method
ms.assetid: bb82a0c5-22b9-4844-9204-7922033d8b07
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7d206e581166fb2bd685e6d4755d56e6d189656c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="ftmbasecreateglobalinterfacetable-method"></a>FtmBase::CreateGlobalInterfaceTable 方法
建立全域介面表 (GIT)。  
  
## <a name="syntax"></a>語法  
  
```  
static HRESULT CreateGlobalInterfaceTable(  
   __out IGlobalInterfaceTable **git  
);  
```  
  
#### <a name="parameters"></a>參數  
 `git`  
 這項作業完成時，全域介面資料表的指標。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 MSDN Library 中的 < COM 參考 > 主題的 「 COM 介面"副主題"IGlobalInterfaceTable 」 主題。  
  
## <a name="requirements"></a>需求  
 **標頭：** ftm.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [FtmBase 類別](../windows/ftmbase-class.md)