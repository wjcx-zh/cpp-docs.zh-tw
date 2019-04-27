---
title: 特性指引最佳化的環境變數
ms.date: 03/14/2018
helpviewer_keywords:
- profile-guided optimizations, environment variables
ms.assetid: f95a6d1e-49a4-4802-a144-092026b600a3
ms.openlocfilehash: 099e57f1ac69223adafe7bec1af4cc3452915e86
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195262"
---
# <a name="environment-variables-for-profile-guided-optimizations"></a>特性指引最佳化的環境變數

有三個會影響在建立映像的測試案例的環境變數 **/ltcg: pgi**特性指引最佳化：

- **PogoSafeMode**指定是否要使用快速模式或 「 安全模式的應用程式程式碼剖析。

- **VCPROFILE_ALLOC_SCALE**新增額外的記憶體，以供分析工具。

- **VCPROFILE_PATH**可讓您指定所使用的.pgc 檔案的資料夾。

**在 PogoSafeMode 和 VCPROFILE_ALLOC_SCALE 環境變數已被取代從 Visual Studio 2015 開始。** 連結器選項[/GENPROFILE 或 /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)並[/USEPROFILE](reference/useprofile.md)為這些環境變數指定相同的連結器行為。

## <a name="pogosafemode"></a>PogoSafeMode

這個環境變數已被取代。 使用**精確**或**NOEXACT**引數 **/GENPROFILE**或是 **/FASTGENPROFILE**來控制這個行為。

清除或設**PogoSafeMode**環境變數，以指定是否要使用快速模式或 「 安全模式的應用程式程式碼剖析在 x86 系統。

特性指引最佳化 (PGO) 的程式碼剖析工作階段有兩個可能的模式：*快速模式*並*安全模式*。 當程式碼剖析處於快速模式時，它會使用**INC**指令增加資料計數器。 **INC**指令更快，但不是安全執行緒。 當程式碼剖析處於安全模式時，它會使用**LOCK INC**指令增加資料計數器。 **LOCK INC**指令具有與相同的功能**INC** ，而且是安全執行緒，但它有低於**INC**指令。

根據預設，PGO 程式碼剖析以快速模式運作。 **PogoSafeMode**是如果您想要使用安全模式下，才需要。

若要執行 PGO 程式碼剖析在安全模式中，您必須使用環境變數**PogoSafeMode**或 連結器參數 **/PogoSafeMode**，取決於系統。 如果您正在執行分析使用 x64 電腦，您必須使用連結器參數。 如果您正在執行 x86 程式碼剖析的電腦，您可以使用連結器設定或切換**PogoSafeMode**環境變數，以在開始最佳化程序之前的任何值。

### <a name="pogosafemode-syntax"></a>PogoSafeMode 語法

> **set PogoSafeMode**[**=**_value_]

設定**PogoSafeMode**為任何值，以啟用安全模式。 設定此選項，而不會清除先前的值，並重新啟用 快速模式的值。

## <a name="vcprofileallocscale"></a>VCPROFILE_ALLOC_SCALE

這個環境變數已被取代。 使用**MEMMIN**並**MEMMAX**引數 **/GENPROFILE**或是 **/FASTGENPROFILE**來控制這個行為。

修改**VCPROFILE_ALLOC_SCALE**環境變數，以變更的記憶體數量配置來保留的設定檔資料。 在罕見的情況下，將不會有足夠的記憶體可支援執行測試案例時，收集分析資料。 在這些情況下，您可以藉由設定增加的記憶體數量**VCPROFILE_ALLOC_SCALE**。 如果您收到錯誤訊息，指出您是否有記憶體不足，無法在測試回合期間，較大值指派給**VCPROFILE_ALLOC_SCALE**，直到在測試執行完成，但沒有記憶體不足錯誤。

### <a name="vcprofileallocscale-syntax"></a>VCPROFILE_ALLOC_SCALE 語法

> **set VCPROFILE_ALLOC_SCALE**[__=__*scale_value*]

*Scale_value*參數是您想要執行測試案例的記憶體數量的縮放比例。  預設為 1。 比方說，這個命令列會將縮放比例設為 2:

`set VCPROFILE_ALLOC_SCALE=2`

## <a name="vcprofilepath"></a>VCPROFILE_PATH

使用**VCPROFILE_PATH**環境變數，以指定要建立的.pgc 檔案的目錄。 根據預設，與所分析的二進位檔相同的目錄中建立的.pgc 檔案。 不過，如果二進位檔的絕對路徑不存在，因為可能的情況下，當您從建置二進位的其中一部電腦上執行設定檔案例時，您可以設定**VCPROFILE_PATH**存在於目標電腦上的路徑。

### <a name="vcprofilepath-syntax"></a>VCPROFILE_PATH 語法

> **set VCPROFILE_PATH**[**=**_path_]

設定*路徑*參數，以在其中新增的.pgc 檔案的目錄路徑。 比方說，這個命令列會將資料夾設定為 C:\profile:

`set VCPROFILE_PATH=c:\profile`

## <a name="see-also"></a>另請參閱

[特性指引最佳化](profile-guided-optimizations.md)<br/>
[/GENPROFILE 和 /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/USEPROFILE](reference/useprofile.md)<br/>
