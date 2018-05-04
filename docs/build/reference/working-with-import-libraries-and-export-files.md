---
title: 使用匯入程式庫和匯出檔案 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- LIB [C++], /DEF option
- import libraries
- LIB [C++], import libraries and export files
- export files
- import libraries, creating
ms.assetid: d8175596-9773-4c2f-959d-b05b065a5161
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc2e5b6b1f2a459d7a00e48ff1aaafff38803871
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="working-with-import-libraries-and-export-files"></a>與匯入程式庫和匯出檔案一起使用
您可以使用 LIB /DEF 選項來建立匯入程式庫和匯出檔案。 連結會使用匯出檔建置程式，其中包含匯出 （通常是動態連結程式庫 (DLL)），並且會使用匯入程式庫來解析參考之其他程式中匯出。  
  
 請注意，是否您在預備步驟中，建立您匯入程式庫建立.dll 之前時，您必須傳遞相同的物件檔案集建置.dll 時為您成功建置匯入程式庫時。  
  
 在大部分情況下，您不需要使用 LIB 來建立您匯入程式庫。 當連結包含匯出的程式 （可執行檔或 DLL） 時，連結會自動建立描述匯出匯入程式庫。 更新版本中，當您連結參考那些匯出的程式，您會指定匯入程式庫。  
  
 不過，當 DLL 匯出至也匯入來源的程式，是否直接或間接，您必須使用 LIB 建立匯入程式庫的其中一個。 當 LIB 建立匯入程式庫時，它也會建立匯出檔案。 連結的 dll 檔時，您必須使用匯出檔。  
  
## <a name="see-also"></a>另請參閱  
 [LIB 參考](../../build/reference/lib-reference.md)