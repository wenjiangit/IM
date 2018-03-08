### Code解析代码

```
/**
 * 进行错误Code的解析，
 * 把网络返回的Code值进行统一的规划并返回为一个String资源
 *
 * @param model    RspModel
 * @param callback DataSource.FailedCallback 用于返回一个错误的资源Id
 */
public static void decodeRspCode(RspModel model, DataSource.FailedCallback callback) {
    if (model == null)
        return;

    // 进行Code区分
    switch (model.getCode()) {
        case RspModel.SUCCEED:
            return;
        case RspModel.ERROR_SERVICE:
            decodeRspCode(R.string.data_rsp_error_service, callback);
            break;
        case RspModel.ERROR_NOT_FOUND_USER:
            decodeRspCode(R.string.data_rsp_error_not_found_user, callback);
            break;
        case RspModel.ERROR_NOT_FOUND_GROUP:
            decodeRspCode(R.string.data_rsp_error_not_found_group, callback);
            break;
        case RspModel.ERROR_NOT_FOUND_GROUP_MEMBER:
            decodeRspCode(R.string.data_rsp_error_not_found_group_member, callback);
            break;
        case RspModel.ERROR_CREATE_USER:
            decodeRspCode(R.string.data_rsp_error_create_user, callback);
            break;
        case RspModel.ERROR_CREATE_GROUP:
            decodeRspCode(R.string.data_rsp_error_create_group, callback);
            break;
        case RspModel.ERROR_CREATE_MESSAGE:
            decodeRspCode(R.string.data_rsp_error_create_message, callback);
            break;
        case RspModel.ERROR_PARAMETERS:
            decodeRspCode(R.string.data_rsp_error_parameters, callback);
            break;
        case RspModel.ERROR_PARAMETERS_EXIST_ACCOUNT:
            decodeRspCode(R.string.data_rsp_error_parameters_exist_account, callback);
            break;
        case RspModel.ERROR_PARAMETERS_EXIST_NAME:
            decodeRspCode(R.string.data_rsp_error_parameters_exist_name, callback);
            break;
        case RspModel.ERROR_ACCOUNT_TOKEN:
            Application.showToast(R.string.data_rsp_error_account_token);
            instance.logout();
            break;
        case RspModel.ERROR_ACCOUNT_LOGIN:
            decodeRspCode(R.string.data_rsp_error_account_login, callback);
            break;
        case RspModel.ERROR_ACCOUNT_REGISTER:
            decodeRspCode(R.string.data_rsp_error_account_register, callback);
            break;
        case RspModel.ERROR_ACCOUNT_NO_PERMISSION:
            decodeRspCode(R.string.data_rsp_error_account_no_permission, callback);
            break;
        case RspModel.ERROR_UNKNOWN:
        default:
            decodeRspCode(R.string.data_rsp_error_unknown, callback);
            break;
    }
}

private static void decodeRspCode(@StringRes final int resId,
                                  final DataSource.FailedCallback callback) {
    if (callback != null)
        callback.onDataNotAvailable(resId);
}


/**
 * 收到账户退出的消息需要进行账户退出重新登录
 */
private void logout() {

}
```