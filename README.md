# Nativescript - Angular - JWT


- Angular v6+ and RxJS v6+ -> v1.0

The library provides an `HttpInterceptor` which automatically attaches a [JSON Web Token](https://jwt.io) to `HttpClient` requests.

## Installation

```bash
# installation with tns
tns install slejnej/ns-angular-jwt
```

## Usage
1. make sure you have credentials from your any OAuth2 service
2. create your injectable `AuthGuard` service in app root as follows
```
// file - auth-guard.service
import all_needed_used_and_injected!!!

@Injectable()
export class AuthGuard implements CanActivate {

    subscription: Subscription;
    
    constructor(private routerExtensions: RouterExtensions, protected authService: AuthService,
        protected userService: UserService, private storage: SecureStorageService) { }
    
    canActivate() {
        if (this.authService.isAuthenticated()) {
            console.log('guard OK');
            return true;
        }
        else {
            console.log('guard FAIL');
            // logout user and redirect
            return false;
        }
    }
    
```
3. in your `app-routing.module.ts` check that you have defined auth providers as:
```
import { AuthGuard } from "~/auth-guard.service";
export const authProviders = [
  AuthGuard
];
```
4. create new `token.interceptor.ts`
```

```