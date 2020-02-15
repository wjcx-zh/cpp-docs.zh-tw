---
title: /ERRORREPORT (dumpbin.exe)
description: Microsoft DUMPBIN utility/ERRORREPORT 命令列選項的參考。
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT
helpviewer_keywords:
- -ERRORREPORT dumpbin option
- ERRORREPORT dumpbin option
- /ERRORREPORT dumpbin option
ms.assetid: 51178c43-4f95-4fda-8f97-50a257d1c948
ms.openlocfilehash: 665b4b1e7c01de4a1fcd848a9e6b36ddbf2944c9
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257672"
---
# <a name="errorreport-dumpbinexe"></a>/ERRORREPORT (dumpbin.exe)

> [!NOTE]
> /ERRORREPORT 選項已被取代。 從 Windows Vista 開始，錯誤報表是由[Windows 錯誤報告（WER）](/windows/win32/wer/windows-error-reporting)設定所控制。

## <a name="syntax"></a>語法

> **/ERRORREPORT**\[**NONE** \|**提示**字元 \|**佇列**\|**傳送**]

## <a name="remarks"></a>備註

Windows 錯誤報告的服務設定會覆寫 **/ERRORREPORT**引數。 如果 Windows 錯誤報告啟用報告功能，DUMPBIN 會自動將內部錯誤的報告傳送給 Microsoft。 如果 Windows 錯誤報告停用，則不會傳送任何報表。

## <a name="see-also"></a>另請參閱

[DUMPBIN 選項](dumpbin-options.md)
