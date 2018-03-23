---
title: 特性指引最佳化的環境變數 |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- profile-guided optimizations, environment variables
ms.assetid: f95a6d1e-49a4-4802-a144-092026b600a3
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 701f0292d9960801139abc698946122718247645
ms.sourcegitcommit: ee7d74683af7631441c8c7f65ef5ceceaee4a5ee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="environment-variables-for-profile-guided-optimizations"></a>特性指引最佳化的環境變數

有三個會影響測試案例，以建立映像上的環境變數**/ltcg: pgi**用於特性指引最佳化：

- **PogoSafeMode**指定是否要使用快速模式或 「 安全模式的應用程式程式碼剖析。

- **VCPROFILE_ALLOC_SCALE**新增額外的記憶體，以供分析工具。

- **VCPROFILE_PATH**可讓您指定所使用的.pgc 檔案的資料夾。

**已被取代從 Visual Studio 2015 開始在 PogoSafeMode 和 VCPROFILE_ALLOC_SCALE 環境變數。** 連結器選項[/GENPROFILE 或 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)和[/USEPROFILE](useprofile.md)為這些環境變數指定相同的連結器行為。

## <a name="pogosafemode"></a>PogoSafeMode

這個環境變數已被取代。 使用**精確**或**NOEXACT**引數**/GENPROFILE**或**/FASTGENPROFILE**控制這個行為。

清除或設定**PogoSafeMode**環境變數，以指定是否要使用快速模式或 「 安全模式，在 x86 上分析應用程式的系統。

特性指引最佳化 (PGO) 的程式碼剖析工作階段有兩個可能的模式：*快速模式*和*安全模式*。 當程式碼剖析為快速模式時，它會使用**INC**指令，以便增加資料計數器。 **INC**指令更快，但不是安全執行緒。 當程式碼剖析處於安全模式時，它會使用**鎖定 INC**指令，以便增加資料計數器。 **鎖定 INC**指令具有相同的功能**INC**指令，且具備執行緒安全，但是它低於**INC**指令。

根據預設，PGO 分析在快速模式下運作。 **PogoSafeMode**是如果您想要使用安全模式，才需要。

若要執行 PGO 分析在安全模式中，您必須使用環境變數**PogoSafeMode**或連結器參數**/PogoSafeMode**，取決於系統上。 如果您正在執行分析在 x64 電腦，您必須使用連結器參數。 如果您正在執行 x86 程式碼剖析的電腦，您可以使用連結器參數，或是設定**PogoSafeMode**環境變數，以啟動最佳化處理序之前的任何值。

### <a name="pogosafemode-syntax"></a>PogoSafeMode 語法

> **set PogoSafeMode**[**=**_value_]

設定**PogoSafeMode**為任何值，以啟用安全模式。 沒有要清除先前的值，然後重新啟用 快速模式的值設定。

## <a name="vcprofileallocscale"></a>VCPROFILE_ALLOC_SCALE

這個環境變數已被取代。 使用**MEMMIN**和**MEMMAX**引數**/GENPROFILE**或**/FASTGENPROFILE**控制這個行為。

修改**VCPROFILE_ALLOC_SCALE**環境變數，以變更資料的記憶體量配置以保留的設定檔資料。 在罕見的情況下，則不會有記憶體不足，無法支援執行測試案例時，收集分析資料。 在這些情況下，您可以增加的記憶體數量，藉由設定**VCPROFILE_ALLOC_SCALE**。 如果您收到錯誤訊息表示您有記憶體不足，無法在測試回合期間，較大值指派給**VCPROFILE_ALLOC_SCALE**，直到執行完成，但沒有記憶體不足錯誤測試。

### <a name="vcprofileallocscale-syntax"></a>VCPROFILE_ALLOC_SCALE 語法

> **set VCPROFILE_ALLOC_SCALE**[__=__*scale_value*]

*Scale_value*參數是您想要執行測試案例的記憶體容量的縮放比例。  預設為 1。 例如，此命令列設定的縮放比例 2:

`set VCPROFILE_ALLOC_SCALE=2`

## <a name="vcprofilepath"></a>VCPROFILE_PATH

使用**VCPROFILE_PATH**環境變數來指定要建立的.pgc 檔案的目錄。 根據預設，.pgc 檔案的建立與所分析的二進位檔相同的目錄中。 不過，如果二進位檔的絕對路徑不存在，作為可能的情況下，當您從建置二進位的一部電腦上執行設定檔的案例，您可以設定**VCPROFILE_PATH**存在於目標電腦上的路徑。

### <a name="vcprofilepath-syntax"></a>VCPROFILE_PATH 語法

> **set VCPROFILE_PATH**[**=**_path_]

設定*路徑*參數，以在其中新增.pgc 檔案的目錄路徑。 例如，此命令列將資料夾設定為 C:\profile:

`set VCPROFILE_PATH=c:\profile`

## <a name="see-also"></a>另請參閱

[特性指引最佳化](../../build/reference/profile-guided-optimizations.md)<br/>
[/GENPROFILE 和 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/USEPROFILE](useprofile.md)<br/>
