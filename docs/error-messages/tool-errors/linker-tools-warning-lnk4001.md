---
title: 連結器工具警告 LNK4001 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4001
dev_langs:
- C++
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: acf65c00c5c039769a05e009dcfe46ea42633ac4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300354"
---
# <a name="linker-tools-warning-lnk4001"></a>連結器工具警告 LNK4001
指定; 任何目的檔使用程式庫  
  
 連結器傳遞了一個或多個.lib 檔案，但沒有.obj 檔案。  
  
 連結器不能存取資訊的.lib 檔案中，它都能夠存取.obj 檔案中，因為這則警告指出您必須明確指定其他連結器選項。 例如，您可能需要指定[/機器](../../build/reference/machine-specify-target-platform.md)， [/out](../../build/reference/out-output-file-name.md)，或[/ENTRY](../../build/reference/entry-entry-point-symbol.md)選項。