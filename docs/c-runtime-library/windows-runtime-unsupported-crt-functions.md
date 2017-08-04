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
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 0eb057f9d229c659f339f996d1ff38f65fd2e018
ms.openlocfilehash: be461857f4aa1625094b20a2241ab15853d2aa81
ms.contentlocale: zh-tw
ms.lasthandoff: 06/01/2017

---
# <a name="windows-runtime-unsupported-crt-functions"></a>Windows 執行階段不支援的 CRT 函式
許多 C 執行階段 (CRT) API 都不能用於在「Windows 執行階段」中執行的 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式。 這些應用程式會使用 /ZW 編譯器旗標建置。 如需不支援的 CRT 函式清單，請參閱 [/ZW 不支援的 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
 所有的 CRT API 都會在本文件的[依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)一節中描述。  
  
## <a name="see-also"></a>另請參閱  
 [依類別區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)   
 [依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)
