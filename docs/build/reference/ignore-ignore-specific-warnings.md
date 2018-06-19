---
title: -忽略 （忽略特定的警告） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /OVERWRITE
dev_langs:
- C++
helpviewer_keywords:
- /IGNORE linker option
ms.assetid: 37e77387-8838-4697-898f-d376ac641124
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b096fc12f69fbe637a3067646c20f6d520a9250f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378005"
---
# <a name="ignore-ignore-specific-warnings"></a>/IGNORE (忽略特定的警告)
```  
/IGNORE:warning[,warning]  
```  
  
## <a name="parameters"></a>參數  
 `warning`  
 要隱藏的連結器警告數目 (在 4000 到 4999 的範圍內)。  
  
## <a name="remarks"></a>備註  
 根據預設，LINK 會報告所有警告。 指定**忽略：** `warning`告訴連結器隱藏特定的警告編號。 若要忽略多個警告，請以逗號分隔警告編號。  
  
 連結器不允許忽略某些警告。 下表列出不隱藏的警告**忽略**:  
  
|連結器警告||  
|--------------------|-|  
|LNK4017|`keyword` 陳述式在目標平台中不受支援；已忽略|  
|[LNK4044](../../error-messages/tool-errors/linker-tools-warning-lnk4044.md)|無法辨認的選項 '`option`'；已忽略|  
|LNK4062|'`option`'不相容的'`architecture`' 目標電腦; 已忽略選項|  
|[LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md)|正在忽略 "`option1`"，原因為 "`option2`" 規格|  
|[LNK4086](../../error-messages/tool-errors/linker-tools-warning-lnk4086.md)|進入點 '`function`' 是具有 '`number`' 個位元組引數的 not __stdcall；影像可能無法執行|  
|LNK4088|由於 /FORCE 選項而要產生影像；影像可能無法執行|  
|[LNK4105](../../error-messages/tool-errors/linker-tools-warning-lnk4105.md)|未使用選項 '`option`' 指定引數；正在忽略參數|  
|LNK4203|讀取程式資料庫 '`filename`' 時發生錯誤；會如同沒有偵錯資訊般連結物件|  
|[LNK4204](../../error-messages/tool-errors/linker-tools-warning-lnk4204.md)|'`filename`' 遺漏參考模組的偵錯資訊如同沒有偵錯資訊般連結物件|  
|[LNK4205](../../error-messages/tool-errors/linker-tools-warning-lnk4205.md)|'`filename`' 遺漏參考模組; 的目前偵錯資訊如同沒有偵錯資訊般連結物件|  
|[LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)|找不到先行編譯類型資訊；未連結或覆寫 '`filename`'；會如同沒有偵錯資訊般連結物件|  
|LNK4207|'`filename`' 編譯 /Yc /Yu /Z7，無法建立 PDB; 使用 /Zi 重新編譯，連結物件如同沒有偵錯資訊|  
|LNK4208|'`filename`' 中的 PDB 格式不相容；刪除並重建；會如同沒有偵錯資訊般連結物件|  
|LNK4209|偵錯資訊損毀；重新編譯模組；會如同沒有偵錯資訊般連結物件|  
|[LNK4224](../../error-messages/tool-errors/linker-tools-warning-lnk4224.md)|不再支援 `option`；已忽略|  
|LNK4228|'`option`' DLL 的無效; 已忽略|  
|[LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)|無效的指示詞 /`directive`；已忽略|  
  
 一般情況下，無法忽略的連結器警告表示應該修正的組建失敗、命令列錯誤或組態錯誤。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  在**連結器**資料夾中，選取**命令列**屬性頁。  
  
3.  修改**其他選項**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。