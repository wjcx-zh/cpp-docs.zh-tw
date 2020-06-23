---
title: 更新 WINVER 和 _WIN32_WINNT
description: 何時和如何更新已升級 Visual Studio c + + 專案中的 WINVER 和 _WIN32_WINNT 宏。
ms.date: 06/19/2020
helpviewer_keywords:
- WINVER in an upgraded Visual Studio C++ project
- _WIN32_WINNT in an upgraded Visual Studio C++ project
ms.assetid: 6a1f1d66-ae0e-48a7-81c3-524d8e8f3447
ms.openlocfilehash: a0faed612517bf26cd89473e1aef248fb9e7b33e
ms.sourcegitcommit: 493fd8747f832e1facb9a76c437a25a5c9fb55f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141050"
---
# <a name="update-winver-and-_win32_winnt"></a>更新 WINVER 和 _WIN32_WINNT

當您使用 Windows SDK 時，可以指定您的程式碼可以在哪些版本的 Windows 上執行。 預處理器宏**WINVER**和 **_WIN32_WINNT**指定程式碼所支援的最低作業系統版本。 Visual Studio 和 Microsoft c + + 編譯器支援以 Windows 7 SP1 和更新版本為目標。 舊版工具組包含對 Windows XP SP2、Windows Server 2003 SP1、Vista 和 Windows Server 2008 的支援。 不支援 windows 95、Windows 98、Windows ME、Windows NT 和 Windows 2000。

當您升級較舊的專案時，可能需要更新您的**WINVER**或 **_WIN32_WINNT**宏。 如果它們是針對不支援的 Windows 版本指派的值，您可能會看到與這些宏相關的編譯錯誤。

## <a name="remarks"></a>備註

若要修改宏，請在標頭檔中（例如，在*targetver.h*中，由以 Windows 為目標的某些專案範本所包含）新增下列幾行。

```C
#define WINVER 0x0A00
#define _WIN32_WINNT 0x0A00
```

範例中的宏會設定為以 Windows 10 作業系統的每個版本為目標。 可能的值列在 Windows 標頭檔*sdkddkver.h*中，它會定義每個主要 Windows 版本的宏。 若要建立您的應用程式以支援先前的 Windows 平臺，請包含*winsdkver.h*。 然後，在包含*sdkddkver.h*之前，將**WINVER**和 **_WIN32_WINNT**宏設定為最舊的支援平臺。 以下是 Windows 10 SDK 版本的*sdkddkver.h*的程式碼，它會針對每個主要版本的 windows 編碼值：

```C
//
// _WIN32_WINNT version constants
//
#define _WIN32_WINNT_NT4                    0x0400 // Windows NT 4.0
#define _WIN32_WINNT_WIN2K                  0x0500 // Windows 2000
#define _WIN32_WINNT_WINXP                  0x0501 // Windows XP
#define _WIN32_WINNT_WS03                   0x0502 // Windows Server 2003
#define _WIN32_WINNT_WIN6                   0x0600 // Windows Vista
#define _WIN32_WINNT_VISTA                  0x0600 // Windows Vista
#define _WIN32_WINNT_WS08                   0x0600 // Windows Server 2008
#define _WIN32_WINNT_LONGHORN               0x0600 // Windows Vista
#define _WIN32_WINNT_WIN7                   0x0601 // Windows 7
#define _WIN32_WINNT_WIN8                   0x0602 // Windows 8
#define _WIN32_WINNT_WINBLUE                0x0603 // Windows 8.1
#define _WIN32_WINNT_WINTHRESHOLD           0x0A00 // Windows 10
#define _WIN32_WINNT_WIN10                  0x0A00 // Windows 10
```

如需更精細的版本控制方法，您可以使用*sdkddkver.h*中的 NTDDI 版本常數。 以下是 Windows 10 SDK 版本10.0.18362.0 中*sdkddkver.h*所定義的一些宏：

```C
//
// NTDDI version constants
//
#define NTDDI_WIN7                          0x06010000
#define NTDDI_WIN8                          0x06020000
#define NTDDI_WINBLUE                       0x06030000
#define NTDDI_WINTHRESHOLD                  0x0A000000  /* ABRACADABRA_THRESHOLD */
#define NTDDI_WIN10                         0x0A000000  /* ABRACADABRA_THRESHOLD */
#define NTDDI_WIN10_TH2                     0x0A000001  /* ABRACADABRA_WIN10_TH2 */
#define NTDDI_WIN10_RS1                     0x0A000002  /* ABRACADABRA_WIN10_RS1 */
#define NTDDI_WIN10_RS2                     0x0A000003  /* ABRACADABRA_WIN10_RS2 */
#define NTDDI_WIN10_RS3                     0x0A000004  /* ABRACADABRA_WIN10_RS3 */
#define NTDDI_WIN10_RS4                     0x0A000005  /* ABRACADABRA_WIN10_RS4 */
#define NTDDI_WIN10_RS5                     0x0A000006  /* ABRACADABRA_WIN10_RS5 */
#define NTDDI_WIN10_19H1                    0x0A000007  /* ABRACADABRA_WIN10_19H1*/

#define WDK_NTDDI_VERSION                   NTDDI_WIN10_19H1 /* ABRACADABRA_WIN10_19H1 */

//
// masks for version macros
//
#define OSVERSION_MASK      0xFFFF0000
#define SPVERSION_MASK      0x0000FF00
#define SUBVERSION_MASK     0x000000FF

//
// macros to extract various version fields from the NTDDI version
//
#define OSVER(Version)  ((Version) & OSVERSION_MASK)
#define SPVER(Version)  (((Version) & SPVERSION_MASK) >> 8)
#define SUBVER(Version) (((Version) & SUBVERSION_MASK) )
```

**OSVER**、 **SPVER**和**SUBVER**宏可用於您的程式碼，以控制不同 API 支援層級的條件式編譯。

您可能不會看到所有這些版本的 Windows 都列于您要查看的*sdkddkver.h*中。 這表示您可能使用較舊版本的 Windows SDK。 根據預設，Visual Studio 中的新 Windows 專案會使用 Windows 10 SDK。

> [!NOTE]
> 如果您在應用程式中包含內部 MFC 標頭，則不保證值能夠運作。

您也可以利用 `/D` 編譯器選項，定義此巨集。 如需詳細資訊，請參閱 [/D (Preprocessor Definitions)](../build/reference/d-preprocessor-definitions.md)。

如需這些巨集的意義的相關資訊，請參閱 [使用 Windows 標頭](/windows/win32/WinProg/using-the-windows-headers)。

## <a name="see-also"></a>另請參閱

[Visual C++ 變更歷程記錄](../porting/visual-cpp-change-history-2003-2015.md)
