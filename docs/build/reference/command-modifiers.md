---
title: 命令修飾詞
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, command modifiers
- command modifiers
ms.assetid: b661c432-210f-4f05-bc56-744a46e0fc0b
ms.openlocfilehash: 6131b94a6ee78026b8d5337061a6238df785b64d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824695"
---
# <a name="command-modifiers"></a>命令修飾詞

您可以指定一或多個命令修飾詞，上述命令，選擇性地以空格或定位字元分隔。 如同命令修飾詞必須縮排。

|修飾詞|用途|
|--------------|-------------|
|\@*命令*|可防止命令的顯示。 不會隱藏顯示命令。 根據預設，NMAKE 會回應所有執行的命令。 使用 /S 隱藏顯示整個的 makefile;使用 **。無訊息**隱藏的 makefile 的組件顯示。|
|**-**\[*number*] *command*|關閉 chyba při kontrole*命令*。 根據預設，NMAKE 暫止命令傳回非零結束代碼時。 如果-*數字*會使用 NMAKE 停止如果結束代碼超過*數目*。 空格或定位點不能出現之間虛線和*數目。* 之間必須有至少一個空格或定位字元`number`並*命令*。 若要關閉的錯誤檢查整個 makefile 中; 使用 /I使用 **。忽略**關閉檢查一部分的 makefile 時發生錯誤。|
|**\!** *command*|執行*命令*針對每個相依的檔案若*命令*會使用<strong>$ \* \*</strong> （相依性中的所有相依檔案） 或 **$?** （中的所有相依檔案時間戳記晚於目標相依性）。|

## <a name="see-also"></a>另請參閱

[Makefile 中的命令](commands-in-a-makefile.md)
