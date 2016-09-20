# api-tb-angular

app.module.ts
```typescript
import { ApiModule } from "api-tb-angular";

@NgModule({
  imports: [
    ApiModule
  ]
})
export class AppModule { }
```

app.action.ts
```typescript
import { Action } from "api-tb-angular";

@Action({ key: "app" })
export class AppAction {
  public foo: string;
  public bar: number;
}
```

app.component.ts
```typescript
import { ApiProvider } from "api-tb-angular";

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css'],
  providers: []
})
export class AppComponent {
  constructor(private api: ApiProvider) {

    let action = new AppAction();
    
    action.foo = "lorem";
    action.bar = 42;

    api.error.subscribe(err => {
      console.log(err);
    });

    api.on(TestEvent).subscribe(data => {
      console.log(data);
    });

    api.emit(action);
  }
}
```
