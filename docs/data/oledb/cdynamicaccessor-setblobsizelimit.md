---
title: CDynamicAccessor::SetBlobSizeLimit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDynamicAccessor::SetBlobSizeLimit
- SetBlobSizeLimit
- CDynamicAccessor.SetBlobSizeLimit
- ATL.CDynamicAccessor.SetBlobSizeLimit
- ATL::CDynamicAccessor::SetBlobSizeLimit
dev_langs:
- C++
helpviewer_keywords:
- SetBlobSizeLimit method
ms.assetid: fb8cb85d-f841-408e-a344-37895b10993f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a2fac05c1380e2b612cb39994716387d99bef237
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="cdynamicaccessorsetblobsizelimit"></a>CDynamicAccessor::SetBlobSizeLimit
設定最大 BLOB 大小 （位元組）。  
  
## <a name="syntax"></a>語法  
  
```cpp
      void SetBlobSizeLimit(DBLENGTH nBlobSize);  
```  
  
#### <a name="parameters"></a>參數  
 `nBlobSize`  
 指定 BLOB 的大小上限。  
  
## <a name="remarks"></a>備註  
 設定最大 BLOB 大小 （位元組）;資料行的資料大於此值會被視為 BLOB。 某些提供者 （例如 2 GB) 的資料行提供極大的大小。 而不是嘗試將資料行大小配置記憶體，通常就會嘗試為 Blob 這些資料行繫結。 如此一來，您不需要配置所有記憶體時，但您仍然可以閱讀而不必擔心截斷的所有資料。 不過，有某些情況的下，您可能想強制`CDynamicAccessor`原生資料型別繫結大型的資料行。 若要這樣做，請呼叫`SetBlobSizeLimit`之前先呼叫**開啟**。  
  
 建構函式方法[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)設定成預設值為 8000 個位元組的最大 BLOB 大小。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)