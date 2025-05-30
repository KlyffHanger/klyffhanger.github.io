{% if docsPrefix == 'pe/' %}
{% assign appPrefix = "Klyff PE" %}
{% assign appProject = "flutter_thingsboard_pe_app" %}
{% else %}
{% assign appPrefix = "Klyff" %}
{% assign appProject = "flutter_thingsboard_app" %}
{% endif %}

{{appPrefix}} Mobile Application provides OAuth 2.0 support. With OAuth 2.0 enabled mobile app will display additional sign-in buttons
on the login screen allowing user to authenticate with configured OAuth 2.0 provider.
It can be configured in **OAuth2** settings form by System administrator user.
See [OAuth 2.0 Support](/docs/{{docsPrefix}}user-guide/oauth-2-support/) to understand general OAuth configuration.
In order to enable OAuth in mobile app you should register it in the **Mobile applications** tab of OAuth settings form:

1. As a System administrator user Go to **System Settings** -> **OAuth2**;
2. Expand domains panel;
3. Open **Mobile applications** tab and click **Add application**;
4. Specify you application package (For Android: your own unique Application ID. For iOS: Product bundle identifier.);
5. Remember autogenerated **Application secret** or input your own secret;
6. Finally, to apply changes click **Save** button in bottom right corner of OAuth form;

{% include images-gallery.html imageCollection="oauth2" %}

Additionally, you should modify your mobile app constants.
Open **{{appProject}}** project in your editor/IDE. Edit **lib/constants/app_constants.dart**.

Set value of **thingsboardOAuth2AppSecret** constant to value of **Application secret** field.
Change value of **thingsboardOAuth2CallbackUrlScheme** constant to some unique pkg name, for ex. you can use your application package with **auth** suffix (ex. org.mycompany.myapp.auth):

```dart
abstract class ThingsboardAppConstants {
  ...

  static final thingsboardOAuth2CallbackUrlScheme = 'Your callback url scheme here';

  static final thingsboardOAuth2AppSecret = 'Your app secret here';
}

```

{% capture oauth_2_domain %}
**Note:** Domain name used in **klyffApiEndpoint** constant should match to one of the domains configured in OAuth settings form.
{% endcapture %}
{% include templates/info-banner.md content=oauth_2_domain %}

Edit **android/app/src/main/AndroidManifest.xml**, find and set scheme of **TbWebCallbackActivity** to same value as **thingsboardOAuth2CallbackUrlScheme** constant:

```xml
  ...
        <activity android:name=".TbWebCallbackActivity" >
            <intent-filter android:label="tb_web_auth">
                <action android:name="android.intent.action.VIEW" />
                <category android:name="android.intent.category.DEFAULT" />
                <category android:name="android.intent.category.BROWSABLE" />
                <data android:scheme="Your callback url scheme here" />
            </intent-filter>
        </activity>
  ...
```

To verify your OAuth 2.0 setup run the mobile app.
You should see additional OAuth 2.0 sign-in button(s) on the top of login form.
If your setup is correct you should be able to perform login to app for existing users just via OAuth 2.0 sign-in button(s).

{% include images-gallery.html imageCollection="oauth2-login-buttons" %}

