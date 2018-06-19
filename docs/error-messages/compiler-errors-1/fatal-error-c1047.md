---
title: 嚴重錯誤 C1047 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1047
dev_langs:
- C++
helpviewer_keywords:
- C1047
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce88321173ee2c8cc286f18d8ab8f1bf5ec98e13
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198621"
---
# <a name="fatal-error-c1047"></a>嚴重錯誤 C1047
物件或程式庫檔案 'file' 是使用比其他物件更舊的編譯器建立的，請重建舊物件和程式庫  
  
 如果由 **/LTCG** 所建置的目的檔或程式庫連結在一起，但這些目的檔或程式庫是使用不同版本的 Visual C++ 工具組所建置，則會造成 C1047。  
  
 如果您開始使用新版本的編譯器，但不會執行現有目的檔或程式庫的全新重建，則可能會發生這種情況。  
  
 若要解決 C1047，請重建所有目的檔或程式庫。