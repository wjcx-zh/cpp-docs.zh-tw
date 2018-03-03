---
title: "ComPtr::Reset |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: aa6a46f7-f56b-4fd5-add0-7cea55f7abda
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ad9dd8bc8c180d8a1fd7bf90965349c620eab54b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="comptrreset"></a>ComPtr::Reset
釋放與這個 ComPtr 相關聯的介面指標的所有參考。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned long Reset();  
```  
  
## <a name="return-value"></a>傳回值  
 釋放的參考數目 (若有的話)。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [ComPtr 類別](../windows/comptr-class.md)