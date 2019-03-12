---
title: errno 常數
ms.date: 09/17/2018
f1_keywords:
- ENOEXEC
- ENOMEM
- E2BIG
- STRUNCATE
- ENOENT
- EMFILE
- EBADF
- EDEADLOCK
- EXDEV
- EILSEQ
- EINVAL
- EDOM
- EACCES
- ERANGE
- ENOSPC
- EAGAIN
- EEXIST
- ECHILD
helpviewer_keywords:
- ENOEXEC constant
- EBADF constant
- EAGAIN constant
- EINVAL constant
- ENOENT constant
- errno constants
- E2BIG constant
- EMFILE constant
- EDEADLOCK constant
- ENOSPC constant
- EDOM constant
- ENOMEM constant
- EACCES constant
- EEXIST constant
- STRUNCATE constant
- ERANGE constant
- ECHILD constant
- EXDEV constant
- EILSEQ constant
ms.assetid: 47089258-d5a5-4cd8-b193-223894dea0cf
ms.openlocfilehash: 0e11c11b468ff6e058ccf5c75b000396e0473bfa
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747633"
---
# <a name="errno-constants"></a>errno 常數

## <a name="syntax"></a>語法

```
#include <errno.h>
```

## <a name="remarks"></a>備註

**errno** 值為在發生各種錯誤情況的事件中指派給 [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 的常數。

ERRNO.H 包含 **errno** 值的定義。 不過，ERRNO.H 中所提供的定義並非全都會用於 32 位元的 Windows 作業系統。 ERRNO.H 中的某些值之所以存在，是為了維持與 UNIX 系列作業系統之間的相容性。

32 位元 Windows 作業系統中的 **errno** 值，為 XENIX 系統中 **errno** 值的子集。 因此，**errno** 值和由 Windows 作業系統的系統呼叫所傳回的實際錯誤碼並不一定相同。 若要存取實際的作業系統錯誤碼，請使用包含此值的 [_doserrno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 變數。

支援的 **errno** 值如下：

|常數|說明|
|-|-|
|**ECHILD**|沒有繁衍的處理序。|
|**EAGAIN**|沒有額外的處理序。 建立新處理序的嘗試已失敗，因為已經沒有更多的處理序位置，或是沒有足夠的記憶體，或是已達到最大巢狀層次。|
|**E2BIG**|引數清單太長。|
|**EACCES**|權限遭拒。 檔案的權限設定不允許指定的存取。 此錯誤顯示嘗試存取檔案 (或在某些情況下為存取目錄) 的方式不符合檔案的屬性。<br/><br/>例如，在嘗試讀取未開啟的檔案、開啟現有唯讀檔案以進行寫入，或是開啟目錄而非檔案時，便可能會發生該錯誤。 在 MS-DOS 作業系統 3.0 版或更新版本之下，**EACCES** 也可能表示鎖定或共用違規。<br/><br/>在嘗試對檔案或目錄進行重新命名，或是移除現有目錄時，也可能會發生該錯誤。|
|**EBADF**|檔案編號錯誤。 可能的原因有二：1) 指定的檔案描述元不是有效的值，或不是開啟的檔案。 2) 嘗試寫入以唯讀存取方式開啟的檔案或裝置。|
|**EDEADLOCK**|會發生資源死結。 數學函式的引數沒有位於函式的定義域中。|
|**EDOM**|數學引數。|
|**EEXIST**|檔案存在。 嘗試建立已存在的檔案。 例如，在 **_open** 呼叫中指定 **_O_CREAT** 和 **_O_EXCL** 旗標，但是命名的檔案已經存在。|
|**EILSEQ**|不合法的位元組序列 (例如在 MBCS 字串中)。|
|**EINVAL**|無效引數。 為函式的其中一個引數提供無效的值。 例如，在放置檔案指標 (透過呼叫 **fseek**) 時，為原點所提供的值是位於檔案的開頭之前。|
|**EMFILE**|開啟太多檔案。 沒有更多檔案描述項可用，因此已無法開啟更多檔案。|
|**ENOENT**|無此檔案或目錄。 指定的檔案或目錄不存在或找不到。 在指定的檔案不存在，或是路徑的某個元件並沒有指定現有目錄的情況下，便可能會出現此訊息。|
|**ENOEXEC**|Exec 格式錯誤。 嘗試執行不可執行或是具有無效可執行檔格式的檔案。|
|**ENOMEM**|沒有足夠的核心。 沒有足夠的記憶體可供嘗試的運算子使用。 例如，當沒有足夠記憶體以執行子處理序，或是無法滿足 **_getcwd** 呼叫中的配置要求時，便可能會出現此訊息。|
|**ENOSPC**|裝置無剩餘空間。 裝置上已沒有空間可供寫入 (例如當磁碟已滿時)。|
|**ERANGE**|結果太大。 針對數學函式的引數太大，導致結果部分或完全失去的精確度。 當引數比預期的還要大 (例如，當針對 **_getcwd** 的 *buffer* 引數比預期的還要長) 時，此錯誤也有可能在其他函式中發生。|
|**EXDEV**|跨裝置連結。 嘗試將檔案移至不同的裝置 (使用 **rename** 函式)。|
|**STRUNCATE**|字串複製或串連導致截斷的字串。 請參閱 [_TRUNCATE](../c-runtime-library/truncate.md)。

下列值支援與 Posix 之間的相容性。 它們在非 Posix 系統上為必要值。

```C
#define E2BIG /* argument list too long */
#define EACCES /* permission denied */
#define EADDRINUSE /* address in use */
#define EADDRNOTAVAIL /* address not available */
#define EAFNOSUPPORT /* address family not supported */
#define EAGAIN /* resource unavailable try again */
#define EALREADY /* connection already in progress */
#define EBADF /* bad file descriptor */
#define EBADMSG /* bad message */
#define EBUSY /* device or resource busy */
#define ECANCELED /* operation canceled */
#define ECHILD /* no child process */
#define ECONNABORTED /* connection aborted */
#define ECONNREFUSED /* connection refused */
#define ECONNRESET /* connection reset */
#define EDEADLK /* resource deadlock would occur */
#define EDESTADDRREQ /* destination address required */
#define EDOM /* argument out of domain */
#define EEXIST /* file exists */
#define EFAULT /* bad address */
#define EFBIG /* file too large */
#define EHOSTUNREACH /* host unreachable */
#define EIDRM /* identifier removed */
#define EILSEQ /* illegal byte sequence */
#define EINPROGRESS /* operation in progress */
#define EINTR /* interrupted */
#define EINVAL /* invalid argument */
#define EIO /* io error */
#define EISCONN /* already connected */
#define EISDIR /* is a directory */
#define ELOOP /* too many synbolic link levels */
#define EMFILE /* too many files open */
#define EMLINK /* too many links */
#define EMSGSIZE /* message size */
#define ENAMETOOLONG /* filename too long */
#define ENETDOWN /* network down */
#define ENETRESET /* network reset */
#define ENETUNREACH /* network unreachable */
#define ENFILE /* too many files open in system */
#define ENOBUFS /* no buffer space */
#define ENODATA /* no message available */
#define ENODEV /* no such device */
#define ENOENT /* no such file or directory */
#define ENOEXEC /* executable format error */
#define ENOLCK /* no lock available */
#define ENOLINK /* no link */
#define ENOMEM /* not enough memory */
#define ENOMSG /* no message */
#define ENOPROTOOPT /* no protocol option */
#define ENOSPC /* no space on device */
#define ENOSR /* no stream resources */
#define ENOSTR /* not a stream */
#define ENOSYS /* function not supported */
#define ENOTCONN /* not connected */
#define ENOTDIR /* not a directory */
#define ENOTEMPTY /* directory not empty */
#define ENOTRECOVERABLE /* state not recoverable */
#define ENOTSOCK /* not a socket */
#define ENOTSUP /* not supported */
#define ENOTTY /* inappropriate io control operation */
#define ENXIO /* no such device or address */
#define EOPNOTSUPP /* operation not supported */
#define EOTHER /* other */
#define EOVERFLOW /* value too large */
#define EOWNERDEAD /* owner dead */
#define EPERM /* operation not permitted */
#define EPIPE /* broken pipe */
#define EPROTO /* protocol error */
#define EPROTONOSUPPORT /* protocol not supported */
#define EPROTOTYPE /* wrong protocol type */
#define ERANGE /* result out of range */
#define EROFS /* read only file system */
#define ESPIPE /* invalid seek */
#define ESRCH /* no such process */
#define ETIME /* stream timeout */
#define ETIMEDOUT /* timed out */
#define ETXTBSY /* text file busy */
#define EWOULDBLOCK /* operation would block */
#define EXDEV /* cross device link */
```

## <a name="see-also"></a>另請參閱

[全域常數](../c-runtime-library/global-constants.md)
