---
title: 連結器工具警告 LNK4020 |Microsoft 文件
ms.custom: ''
ms.date: 05/29/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4020
dev_langs:
- C++
helpviewer_keywords:
- LNK4020
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e55239b90910f6c151949c53939d4f8ed7c15c5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34570684"
---
# <a name="linker-tools-warning-lnk4020"></a>連結器工具警告 LNK4020

> 中的類型記錄 '*filename*' 已損毀; 無法從偵錯工具存取某些符號和類型

PDB 檔案*filename*已損毀的類型記錄。

此問題通常是次要其他組建問題;這是第一次報告的組建問題，除非處理其他錯誤和警告第一次。 如果這是第一個回報的問題，您可能需要清除組建目錄，並重建專案。 如果您使用的平行建置程序，請參閱序列化您的組建時，如果持續發生錯誤。