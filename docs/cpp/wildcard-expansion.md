---
title: 萬用字元展開 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _setargv
dev_langs:
- C++
helpviewer_keywords:
- asterisk wildcard
- _setargv function
- command line [C++], processing arguments
- command line [C++], wildcards
- command-line wildcards
- question mark, wildcard
ms.assetid: 1a543398-607b-4404-93d1-45d290bde638
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f4de54cbbe978534a42dcb9cbfa677eb1597aa5
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939132"
---
# <a name="wildcard-expansion"></a>萬用字元展開
## <a name="microsoft-specific"></a>Microsoft 特定的  
 您可以在命令列上使用問號 (?) 和星號 (*) 等萬用字元來指定檔案名稱和路徑引數。  
  
 命令列引數都由呼叫的常式`_setargv`(或`_wsetargv`寬字元環境中)，預設不會為個別的字串中展開萬用字元`argv`字串陣列。 如需有關如何啟用萬用字元展開的詳細資訊，請參閱[展開萬用字元引數](../c-language/expanding-wildcard-arguments.md)。  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [main：程式啟動](../cpp/main-program-startup.md)