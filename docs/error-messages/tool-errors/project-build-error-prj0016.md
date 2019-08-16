---
title: 專案建置錯誤 PRJ0016
ms.date: 11/04/2016
f1_keywords:
- PRJ0016
helpviewer_keywords:
- PRJ0016
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
ms.openlocfilehash: 6733ef1f390f2ff377356dda3f7cd3ebfe10cc2b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509878"
---
# <a name="project-build-error-prj0016"></a>專案建置錯誤 PRJ0016

使用者的安全性設定會使進程無法建立。 這些是建立的必要設定。

您以沒有許可權可使用進程建立進程的使用者身分登入。 您必須變更此使用者帳戶的許可權等級, 或洽詢您的帳戶管理員。

如果已設定下列登錄機碼, 也可能會發生此錯誤:

\\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun

若要解決此錯誤, 請刪除 RestrictRun 鍵。 如果需要此登錄機碼, 請將**vcspawn**附加至機碼中的專案清單。

造成此錯誤的另一個原因是, 您的原則設定不會在登錄機碼 HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun 下包含 VCSpawn, 做為此使用者帳戶的允許視窗程式。

如需其他資訊, 請參閱[遵循系統原則設定](/previous-versions/windows/desktop/Policy/adhering-to-system-policy-settings), 在「僅執行允許的 Windows 應用程式」一節中。