---
title: "system 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- system function
ms.assetid: 0786ccdc-20cd-4d96-b3d8-3230507c3066
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
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
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: b504aedc5ad11edf40d7b797529065757dfb58e6
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="system-function"></a>system 函式
**ANSI 4.10.4.5** 字串是由 **system** 函式執行的內容與執行模式  
  
 **system** 函式會執行內部作業系統命令，或從 C 程式 (而不是從命令列) 執行 .EXE、.COM (Windows NT 中的 .CMD) 或 .BAT 檔案。  
  
 系統函式會尋找命令解譯器，通常是 Windows NT 作業系統中的 CMD.EXE，或者 Windows 中的 COMMAND.COM。 系統函式接著會將引數字串傳遞給命令解譯器。  
  
 如需詳細資訊，請參閱 [system，_wsystem](../c-runtime-library/reference/system-wsystem.md)。  
  
## <a name="see-also"></a>另請參閱  
 [程式庫函式](../c-language/library-functions.md)
