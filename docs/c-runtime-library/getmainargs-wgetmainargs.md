---
title: "__getmainargs、__wgetmainargs | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- __wgetmainargs
- __getmainargs
apilocation:
- msvcr100.dll
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr110.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- __wgetmainargs
- __getmainargs
dev_langs:
- C++
helpviewer_keywords:
- __wgetmainargs
- __getmainargs
ms.assetid: f72f54eb-9509-4bdf-8752-40fc49055439
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: bd386aba0f5693538d9aae61bcf7c2384b6052bd
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="getmainargs-wgetmainargs"></a>__getmainargs、__wgetmainargs
叫用命令列剖析，並將 `main()` 的引數複製回傳入的指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
int __getmainargs(  
    int * _Argc,   
   char *** _Argv,   
   char *** _Env,   
   int _DoWildCard,  
_startupinfo * _StartInfo);  
  
 int __wgetmainargs (  
   int *_Argc,  
   wchar_t ***_Argv,  
   wchar_t ***_Env,  
   int _DoWildCard,  
   _startupinfo * _StartInfo)  
  
```  
  
#### <a name="parameters"></a>參數  
 `_Argc`  
 包含 `argv` 之後引數數目的整數。 `argc` 參數永遠會大於或等於 1。  
  
 `_Argv`  
 以 null 終止之字串的陣列，表示由程式的使用者所輸入的命令列引數。 依照慣例，`argv[0]` 是對程式叫用的命令，argv[1] 是第一個命令列引數，依此類推，直到 argv[argc]，其永遠為 NULL。 第一個命令列引數一定是 `argv[1]`，而最後一個是 `argv[argc - 1]`。  
  
 `_Env`  
 字串陣列，表示在使用者環境中設定的變數。 這個陣列由 NULL 項目終止。  
  
 `_DoWildCard`  
 整數，如果設定為 1 會在命令列引數中展開萬用字元，或設為 0 不執行任何動作。  
  
 `_StartInfo`  
 要傳遞給 CRT DLL 的其他資訊。  
  
## <a name="return-value"></a>傳回值  
 如果成功則傳回 0，如果失敗則為負值。  
  
## <a name="remarks"></a>備註  
 在非寬字元的平台上使用 `__getmainargs`，在寬字元 (Unicode) 平台上使用 `__wgetmainargs`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|__getmainargs|internal.h|  
|__wgetmainargs|internal.h|
