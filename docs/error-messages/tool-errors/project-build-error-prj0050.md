---
title: 專案建置錯誤 PRJ0050
ms.date: 11/04/2016
f1_keywords:
- PRJ0050
helpviewer_keywords:
- PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
ms.openlocfilehash: ec2490bad70d2b2eb72cbb48771900f09f8c2f67
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62226487"
---
# <a name="project-build-error-prj0050"></a>專案建置錯誤 PRJ0050

無法註冊輸出。 請確定您有適當的權限可以修改登錄。

視覺效果C++建置系統無法註冊組建 （dll 或.exe） 的輸出。 您必須修改登錄的系統管理員身分登入。

如果您要建置 dll，您可以嘗試登錄以手動方式使用 regsvr32.exe 此.dll 檔，這應該會顯示組建的失敗原因的相關資訊。

如果您未建立.dll，查看組建記錄檔中的命令，將導致錯誤。