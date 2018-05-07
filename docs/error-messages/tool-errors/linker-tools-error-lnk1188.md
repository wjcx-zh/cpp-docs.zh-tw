---
title: 連結器工具錯誤 LNK1188 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1188
dev_langs:
- C++
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e31943ae253a332576fba73102db410b103a0096
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1188"></a>連結器工具錯誤 LNK1188
BADFIXUPSECTION:: 無效的修復目標 'symbol';可能為零長度 > 一節  
  
 VxD 連結期間，重新配置的目標沒有 > 一節。 與 LINK386 （較舊版本），（MASM 群組指示詞所產生） 的 OMF 群組記錄可能已用來結合零長度區段與另一個非零長度的區段。 COFF 格式不支援的 GROUP 指示詞和長度為零章節。 連結會自動將此類型的 OMF 物件轉換成 COFF，可能會發生這個錯誤。