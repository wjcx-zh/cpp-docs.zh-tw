---
title: 資源編譯器錯誤 RC2144 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2144
dev_langs:
- C++
helpviewer_keywords:
- RC2144
ms.assetid: 1b3ff39a-92cd-4a04-b1a3-b1fa6a805813
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8b6f83f937e881cdee16c22120e6ac1839f7ad76
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-error-rc2144"></a>資源編譯器錯誤 RC2144
PRIMARY LANGUAGE ID 不是數字  
  
 PRIMARY LANGUAGE ID 必須是十六進位語言 ID。 請參閱[語言和國家/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)中*執行階段程式庫參考*有效語言 Id 的清單。  
  
 如果已在 .RC 檔案中使用工具加入和刪除資源，也會發生此錯誤。 若要修正這個問題，請在文字編輯器中開啟 .RC 檔案，並以手動方式清除任何未使用的資源。