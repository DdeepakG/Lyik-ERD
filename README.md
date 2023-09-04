# Lyik-ERD
## Mermaid.live

erDiagram
    SHARE-UI ||--|| SHARE-BLoC : ""
    SHARE-BLoC ||--|| DB-SVC:""
    SHARE-BLoC ||--|| PROFILE-SVC:""
    SHARE-BLoC ||--|| LANGUAGE-SVC:""
    LOGIN-UI ||--|| LOGIN-BLoC:""
    LOGIN-UI ||--|| PHONE-AUTH-BLoC:""
    PHONE-AUTH-BLoC ||--|| AUTH-SVC:""
    LOGIN-BLoC ||--|| LANGUAGE-SVC:""
    PROFILE-UI ||--|| MEMBER-LIST-BLoC:""
    PROFILE-UI ||--|| PROFILE-BLoC:""
    PROFILE-UI ||--||OTHER-INFO-BLoC :""
    PROFILE-UI ||--|| VERIFY-EMAIL-UI:""
    MEMBER-LIST-BLoC ||--||MEMBER-PROFILE-SVC:""
    MEMBER-PROFILE-SVC ||--|| DB-SVC:""
    MEMBER-LIST-BLoC ||--||DB-SVC:""
    PROFILE-SVC ||--||OTHER-INFO-BLoC :""
    DB-SVC ||--||OTHER-INFO-BLoC :""
    OTHER-INFO-BLoC ||--|| LANGUAGE-SVC:""
    VERIFY-EMAIL-UI ||--|| VERIFY-EMAIL-BLoC:""
    VERIFY-EMAIL-BLoC ||--|| VERIFY-EMAIL-SVC:""
    DB-SVC ||--||VERIFY-EMAIL-SVC :""
    VERIFY-EMAIL-BLoC ||--|| LANGUAGE-SVC:""

    SHARE-UI{
       func DisplayShareableItems
       func SelectUnselectUI
       func DisplayPreview
       func ShareOptions "singlePdf,multiplePdfs,originalFiles"
       func DisplayMessage
    }
    SHARE-BLoC{
        func GetActiveProfile
        func PrepareShareableItems "fetch,organize"
        func HandleItemSelection    "select/unselect items"
        func PreparePreview
        func PrepareShareFiles
        func Share
    }

    LOGIN-UI{
        func InputMobileNumber "restrict 10 digit"
        func CountryCodeSelection
        func TnCApproval "mandatory selection"
        func PrivacyPolicyApproval "mandatory selection"
        func InputOtp
        func ResendTimer
        func ResendOtp
        func DisplayMessage
    }
    LOGIN-BLoC{
        func GetMobileNumber
        func GetCountryCode
        func RequestOTP "send/resend"
        func GetTnCUrl
        func GetPrivacyPolicyUrl
    }

    PHONE-AUTH-BLoC{
        func GetInputOTP
        func SubmitOTP
    }

    PROFILE-UI{
        func DisplayAllProfiles
        func SelectProfile "switch active profile"
        func AddEditProfile
        func EmailVerify
        func DeleteProfile
        func DisplayMessage
    }

    PROFILE-BLoC{
        func SwitchActiveProfile
    }

    MEMBER-LIST-BLoC{
        func FetchAllProfiles
        func DeleteProfile
    }
    OTHER-INFO-BLoC{
        func GetCurrentProfile
        func HandleDataChanges "form field input changes"
        func SaveProfile
    }

    VERIFY-EMAIL-UI{
        func InputOrDisplayEmail "check email format"
        func InputOTP
        func ResendOTP
        func DisplayMessage
    }

    VERIFY-EMAIL-BLoC{
        func GetEmail "user input"
        func GetCurrentProfile
        func CheckVerifyLaterTimestamp
        func CheckEmailAvailability
        func CheckVerificationStatus
        func HandleVerifyLater
        func SendOTP
        func VerifyOTP
        func SaveEmail
    } 

    VERIFY-EMAIL-SVC{
        func SendOTPMail
        func UpdateVerifyLaterTimestamp
        func GetVerifyLaterTimestamp
    }

    PROFILE-SVC{
        func GetCurrentProfileInfo 
    } 

    MEMBER-PROFILE-SVC{
        func GetAllProfiles
    }

    AUTH-SVC{
        func UserSignInSignUp
    }

    DB-SVC{
        func DBOperations "It's DB Repository"
    }
    
