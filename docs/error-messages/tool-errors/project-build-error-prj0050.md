---
title: 專案建置錯誤 PRJ0050
ms.date: 11/04/2016
f1_keywords:
- PRJ0050
helpviewer_keywords:
- PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
ms.openlocfilehash: 56e092b5f7c33ad9543951621b2a9d8f6992331f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191986"
---
# <a name="project-build-error-prj0050"></a>專案建置錯誤 PRJ0050

無法註冊輸出。 請確定您有適當的許可權可修改登錄。

Visual C++ build system 無法註冊組建的輸出（dll 或 .exe）。 您必須以系統管理員的身分登入，才能修改登錄。

如果您要建立 .dll，可以嘗試使用 regsvr32 手動註冊 .dll，這應該會顯示組建失敗原因的相關資訊。

如果您不是建立 .dll，請查看導致錯誤的命令組建記錄檔。
