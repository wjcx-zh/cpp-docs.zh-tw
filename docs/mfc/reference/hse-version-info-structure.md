---
title: "HSE_VERSION_INFO 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- HSE_VERSION_INFO
dev_langs:
- C++
helpviewer_keywords:
- HSE_VERSION_INFO structure [MFC]
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 108f826ffaa17de65dafe246ab6724fac2b134f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="hseversioninfo-structure"></a>HSE_VERSION_INFO 結構
`pVer` 成員函式的 `CHttpServer::GetExtensionVersion` 參數會指向這個結構。 它提供 ISA 版本號碼和 ISA 的文字描述。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct _HSE_VERSION_INFO {  
    DWORD dwExtensionVersion;  
    CHAR lpszExtensionDesc[HSE_MAX_EXT_DLL_NAME_LEN];  
} HSE_VERSION_INFO, *LPHSE_VERSION_INFO;  
```  
  
#### <a name="parameters"></a>參數  
 *dwExtensionVersion*  
 ISA 版本號碼  
  
 *lpszExtensionDesc*  
 ISA 的文字描述。 預設實作提供預留位置文字；覆寫 `CHttpServer::GetExtensionVersion` 以提供您自己的描述。  
  
## <a name="requirements"></a>需求  
 **標頭：** httpext.h  
  
## <a name="see-also"></a>請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

