---
title: 專案建置錯誤 PRJ0050 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0050
dev_langs:
- C++
helpviewer_keywords:
- PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb3949ea0db2f1667aecf1aeeefd922b192cbf41
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100587"
---
# <a name="project-build-error-prj0050"></a>專案建置錯誤 PRJ0050

無法註冊輸出。 請確定您有適當的權限可以修改登錄。

Visual c + + 建置系統無法註冊組建 （dll 或.exe） 的輸出。 您必須修改登錄的系統管理員身分登入。

如果您要建置 dll，您可以嘗試登錄以手動方式使用 regsvr32.exe 此.dll 檔，這應該會顯示組建的失敗原因的相關資訊。

如果您未建立.dll，查看組建記錄檔中的命令，將導致錯誤。