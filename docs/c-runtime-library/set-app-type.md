---
title: _set_app_type | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _set_app_type
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_app_type
- corecrt_startup/_set_app_type
dev_langs:
- C++
ms.assetid: 1e7fe786-b587-4116-8c05-f7d762350100
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: adfd7344b01360df6af3ccf7a153eda3451d2482
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="setapptype"></a>_set_app_type
在啟動時使用的內部函式會告訴 CRT，應用程式是主控台應用程式或 GUI 應用程式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum _crt_app_type
{
    _crt_unknown_app,
    _crt_console_app,
    _crt_gui_app
} _crt_app_type;

void __cdecl _set_app_type(
    _crt_app_type appType
    ); 
```  
  
## <a name="parameters"></a>參數  
 `appType`  
 指出應用程式類型的值。 可能值為：  
  
|值|描述|  
|----------------|-----------------|  
|_crt_unknown_app|不明應用程式類型。|  
|_crt_console_app|主控台 (命令列) 應用程式。|  
|_crt_gui_app|GUI (Windows) 應用程式。|  
  
## <a name="remarks"></a>備註  
 您通常不需要呼叫此函式。 它是應用程式呼叫 `main` 之前即執行的 C 執行階段啟始程式碼的一部分。
 
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|_set_app_type|process.h|

