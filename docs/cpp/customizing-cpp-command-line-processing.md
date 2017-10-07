---
title: "自訂 c + + 命令列處理 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _setenvp
- _setargv
dev_langs:
- C++
helpviewer_keywords:
- command line [C++], processing
- command-line processing
- startup code, customizing command-line processing
- environment, environment-processing routine
- _setargv function
- command line [C++], processing arguments
- suppressing environment processing
- _setenvp function
ms.assetid: aae01cbb-892b-48b8-8e1f-34f22421f263
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 977ab6f5a7a8dbddf045e83a14127ac979a114a9
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="customizing-c-command-line-processing"></a>自訂 C++ 命令列處理
## <a name="microsoft-specific"></a>Microsoft 特定的  
 如果您的程式不接受命令列引數，您可以隱藏執行命令列處理的程式庫常式用法，藉此稍微節省空間。 這個常式稱為**_setargv**並且中會描述[萬用字元展開](../cpp/wildcard-expansion.md)。 若要隱藏其用途，定義不包含的檔案中做任何動作的常式**主要**函式，並將其命名**_setargv**。 若要呼叫**_setargv**然後符合您定義**_setargv**，且不會載入程式庫版本。  
  
 同樣地，如果您永遠不會存取環境資料表透過`envp`引數，您可以提供您自己空的常式，用以取代**_setenvp**，環境處理常式。 就像**_setargv**函式， **_setenvp**必須宣告為**extern"C"**。  
  
 您的程式可能會呼叫**繁衍**或`exec`系列 C 執行階段程式庫中的常式。 如果是這種情況，您就不應該隱藏環境處理常式，因為這個常式會用來將環境從父處理序傳遞至子處理序。  
  
**END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [main：程式啟動](../cpp/main-program-startup.md)
