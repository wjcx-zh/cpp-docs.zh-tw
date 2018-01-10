---
title: _amsg_exit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _amsg_exit
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords: _amsg_exit
dev_langs: C++
helpviewer_keywords: _amsg_exit
ms.assetid: 146d4faf-d763-43a4-b264-12711196456b
caps.latest.revision: "2"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 42981b60a0a3f53c0887fad45bdd41d7ffd2c308
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="amsgexit"></a>_amsg_exit
發出指定的執行階段錯誤訊息，然後以錯誤碼 255 結束應用程式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void _amsg_exit (  
   int rterrnum  
   )  
```  
  
#### <a name="parameters"></a>參數  
 `rterrnum`  
 系統定義之執行階段錯誤訊息的識別碼。  
  
## <a name="remarks"></a>備註  
 此函式會向主控台應用程式的 **stderr** 發出執行階段錯誤訊息，或在 Windows 應用程式的訊息方塊中顯示訊息。 在偵錯模式中，您可以選擇在結束之前叫用偵錯工具。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|_amsg_exit|internal.h|