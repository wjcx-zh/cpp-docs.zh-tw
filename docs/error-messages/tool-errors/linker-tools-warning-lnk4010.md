---
title: 連結器工具警告 LNK4010 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4010
dev_langs:
- C++
helpviewer_keywords:
- LNK4010
ms.assetid: 2824cf99-4174-4b60-a6e2-c01e9f1ee52d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 266e377a917fe3ce9ae7bae228134f49384e15cb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4010"></a>連結器工具警告 LNK4010
無效的子系統版本號碼號碼。假設預設的子系統版本  
  
 您可以指定映像的子系統版本 ([/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md))。 每個子系統有最低版本需求。 如果指定的版本低於最小值，會發生這個警告，連結器會使用預設子系統。