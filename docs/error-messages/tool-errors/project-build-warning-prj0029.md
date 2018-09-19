---
title: 專案建置警告 PRJ0029 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0029
dev_langs:
- C++
helpviewer_keywords:
- PRJ0029
ms.assetid: f02c09c6-09f3-4d44-8cd4-9a25336be1ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 854120bf6021295348ff2e28b36f7b44007017b1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026003"
---
# <a name="project-build-warning-prj0029"></a>專案建置警告 PRJ0029

專案層級自訂建置步驟的 'Outputs' 屬性未設定。 將略過自訂建置步驟。

未執行自訂建置步驟，因為未指定輸出。

若要解決這個錯誤，請執行下列：

- 從組建中排除之自訂建置步驟。

- 加入輸出。

- 刪除自訂建置步驟之命令的內容。