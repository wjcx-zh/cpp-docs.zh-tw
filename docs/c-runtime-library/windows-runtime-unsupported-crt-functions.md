---
title: Windows 執行階段不支援的 CRT 函式 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- unsupported CRT functions, Windows Runtime
- Windows Runtime, unsupported CRT functions
ms.assetid: bb8386d6-0ef8-460c-88d8-addff009b6f1
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 50a04dc63dfc5fbadce7721f5985e3190cdab506
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="windows-runtime-unsupported-crt-functions"></a>Windows 執行階段不支援的 CRT 函式

許多 C 執行階段 (CRT) API 都不能用於在Windows 執行階段中執行的通用 Windows 平台 (UWP) 應用程式。 這些應用程式會使用 /ZW 編譯器旗標建置。 如需不支援的 CRT 函式清單，請參閱[通用 Windows 平台應用程式不支援 CRT 函式](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

所有的 CRT API 都會在本文件的[依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)一節中描述。

## <a name="see-also"></a>請參閱

[依類別排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)<br/>
[依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
