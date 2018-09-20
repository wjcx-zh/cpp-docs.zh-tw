---
title: Users 群組的成員身分執行 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- PRJ0050
- VCD0047
dev_langs:
- C++
helpviewer_keywords:
- Users Group [C++]
- security [C++], Users Group
- Windows accounts [C++]
- non administrator users [C++]
- user accounts [C++]
- administrator (not running as) [C++]
ms.assetid: e48a03ec-d345-49f6-809a-1a291eecbc81
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34028aa243f4c767751da758e43dab5ecf71c110
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431797"
---
# <a name="running-as-a-member-of-the-users-group"></a>以使用者群組的成員身分執行

本主題說明如何將 Windows 使用者帳戶設定為「使用者群組」的成員 (不同於「系統管理員」群組)，藉由降低受到惡意程式碼感染的機會，以提升安全性。

## <a name="security-risks"></a>安全性風險

以系統管理員身分執行會讓您的系統很容易遭受數種安全性攻擊，例如特洛伊木馬程式和緩衝區滿溢。 由於從網際網路網站下載的惡意程式碼，可能會攻擊您的電腦，因此，只是以系統管理員身分造訪網際網路網站便可能對系統造成損害。 如果攻擊成功了，它會繼承您的系統管理員使用權限，接著，便可以執行諸如刪除所有檔案、重新格式化硬碟，以及建立具有系統管理員存取權的新使用者帳戶等動作。

## <a name="non-administrator-user-groups"></a>非系統管理員使用者群組

程式開發人員常用的 Windows 使用者帳戶必須加入至「使用者群組」或「Power Users 群組」。 程式開發人員也可以加入至「偵錯群組」。 成為「使用者群組」成員，可讓您執行例行工作，其中包括了執行程式和瀏覽網際網路網站，而不會使電腦暴露在不必要的風險中。 做為「Power Users 群組」成員，您還可以執行諸如應用程式安裝、印表機安裝和大多數「控制台」作業工作。 如果需要執行管理工作 (例如升級作業系統或設定系統參數)，您必須登入系統管理員帳戶，才能執行管理工作。 或者，Windows **runas**命令可以用來啟動系統管理權限的特定應用程式。

## <a name="exposing-customers-to-security-risks"></a>使客戶遭受安全性風險

不成為「系統管理員群組」的一部分，對程式開發人員來說特別重要，因為除了可以保護開發用電腦以外，還能避免程式開發人員不慎撰寫需要客戶加入「系統管理員群組」才能執行所開發之應用程式的程式碼。 如果在開發過程中引用需要系統管理員存取權的程式碼，此程式碼將會在執行階段失敗，以通知您應用程式現在需要客戶以系統管理員身分來執行。

## <a name="code-that-requires-administrator-privileges"></a>需要系統管理員使用權限的程式碼

某些程式碼需要系統管理員存取權才能執行。 如果可能的話，應該使用此程式碼的替代方法。 需要系統管理員存取權的程式碼作業範例為：

- 寫入檔案系統的保護區域，例如 Windows 或 Program Files 目錄

- 寫入登錄的保護區域，例如 HKEY_LOCAL_MACHINE

- 在全域組件快取 (GAC) 中安裝組件

一般而言，這些動作會受限於應用程式安裝程式。 這讓使用者只能暫時使用系統管理員狀態。

## <a name="debugging"></a>偵錯

您可以藉由成為「偵錯群組」的成員，以非系統管理員的身分偵錯在 Visual Studio (原生和 Unmanaged) 內啟動的任何應用程式。 這包括使用「附加至處理序」命令，以附加至執行中應用程式的能力。 然而，為了偵錯由不同使用者所啟動的原生或 Managed 應用程式，您必須成為「系統管理員群組」的成員。

## <a name="see-also"></a>另請參閱

[安全性最佳做法](security-best-practices-for-cpp.md)