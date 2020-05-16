#Nestとは

- Nodejsフレームワーク
- TypeScript標準
- 内部ではExpressを使用している(Fastifyに変更できる)
- MVC, REST FULL API, GraphQL API


## /src/main.ts
エントリーポイント  
ここからjavascriptが実行される


```typescript
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  await app.listen(3000);
}
bootstrap();
```

コントローラー、モジュール、サービスで1つ  


## Module

## Controller
どんなURLがきたらどんな値を返すかを書く

```typescript
@Controller
export class AppController {
 @Get() //GETリクエストの時何を返すか
 getHello(){
   return 'Hello'
 }
}
```

@Get('hello')とした場合、example.com/helloのとき実行される
@Controller('base')@Get('hello')とした場合、example.com/base/helloのとき実行される



## Service
クラスの前に@Injectable()をつけて、moduleのproviderに登録することで  
```typescript
constructor(private readonly appService: AppService) {}
```

で使用することができる newしなくて良い



main.tsで  
const app = await NestFactory.create(AppModule);
を実行した時点で  
new AppModule()  
される