---
title: HSE_VERSION_INFO 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- HSE_VERSION_INFO
dev_langs:
- C++
helpviewer_keywords:
- HSE_VERSION_INFO structure [MFC]
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: daf1565c2fe2d7a4620f83b765671fea80502102
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335811"
---
# <a name="hseversioninfo-structure"></a>HSE_VERSION_INFO 結構
此結構指向*Amp;os=&over=&hrd=&opt1*中的參數`CHttpServer::GetExtensionVersion`成員函式。 它提供 ISA 版本號碼和 ISA 的文字描述。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

