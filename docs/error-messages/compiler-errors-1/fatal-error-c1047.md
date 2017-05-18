---
title: "嚴重錯誤 C1047 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1047
dev_langs:
- C++
helpviewer_keywords:
- C1047
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: bee5dd89bf6ef92445466b12d79be5ba39d9cb5b
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="fatal-error-c1047"></a>嚴重錯誤 C1047
物件或程式庫檔案 'file' 是使用比其他物件更舊的編譯器建立的，請重建舊物件和程式庫  
  
 如果由 **/LTCG** 所建置的目的檔或程式庫連結在一起，但這些目的檔或程式庫是使用不同版本的 Visual C++ 工具組所建置，則會造成 C1047。  
  
 如果您開始使用新版本的編譯器，但不會執行現有目的檔或程式庫的全新重建，則可能會發生這種情況。  
  
 若要解決 C1047，請重建所有目的檔或程式庫。
