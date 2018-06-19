---
title: 命令列錯誤 D8037 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8037
dev_langs:
- C++
helpviewer_keywords:
- D8037
ms.assetid: acddaaa0-bd84-426f-a37b-8f680b379c9d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 729a7fedbe1be3acbe7d68d9037b2f9c8b9f9806
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298807"
---
# <a name="command-line-error-d8037"></a>命令列錯誤 D8037
無法建立暫存 il 檔案;舊 il 檔案的初始狀態的暫存目錄  
  
 沒有足夠的空間來建立暫存的編譯器中繼檔案。 若要解決這個錯誤，請移除任何舊的 MSIL 檔案中所指定的目錄**TMP**環境變數。 這些檔案都屬於表單 _CL_hhhhhhhh.ss，其中 h 表示的隨機的十六進位數字，而 ss 表示 IL 檔案的類型。 此外，請務必更新您的電腦使用最新的作業系統修補程式。  
  
## <a name="see-also"></a>另請參閱  
 [命令列錯誤 D8000 至 D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)   
 [編譯器選項](../../build/reference/compiler-options.md)