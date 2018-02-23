---
title: "Windows 執行階段不支援的 CRT 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- unsupported CRT functions, Windows Runtime
- Windows Runtime, unsupported CRT functions
ms.assetid: bb8386d6-0ef8-460c-88d8-addff009b6f1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a2f6b06b45da502e3eba898f2907042afeca65c2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="windows-runtime-unsupported-crt-functions"></a>Windows 執行階段不支援的 CRT 函式
許多 C 執行階段 (CRT) API 都不能用於在Windows 執行階段中執行的通用 Windows 平台 (UWP) 應用程式。 這些應用程式會使用 /ZW 編譯器旗標建置。 如需不支援的 CRT 函式清單，請參閱 [/ZW 不支援的 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
 所有的 CRT API 都會在本文件的[依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)一節中描述。  
  
## <a name="see-also"></a>請參閱  
 [依類別區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)   
 [依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)