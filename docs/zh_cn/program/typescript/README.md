# TypeScript Language
> 记录`Typescript`平时的使用习惯，以及平时遇到问题的处理方法等
---

- # 配置文件读取
  - `Configuration.controllers.ts`
    ```typescript
    import { existsSync, mkdirSync, readFileSync } from "fs";
    import { join } from "path";

    const CONFIG_FOLDER: string = join(__dirname, "../config");
    const CONFIG_FILE: string = join(CONFIG_FOLDER, "./basic.json");

    export class ConfigurationController {
      public constructor() {}
      public Initialize(): Configuration {
        if (this.readConfigurationFile() === undefined) {
          throw new Error(
            `Configuration file is not defined! (path: ${CONFIG_FILE})`,
          );
        }
        return this.readConfigurationFile() as Configuration;
      }
      private configurationFolderExists(): boolean {
        if (!existsSync(CONFIG_FOLDER)) {
          try {
            mkdirSync(CONFIG_FILE);
          } catch (err) {
            throw new Error(err as string);
          }
        }
        return true;
      }
      private configurationFileExists(): boolean {
        if (!this.configurationFolderExists()) {
          throw new Error(
            `Configuration folder is not exists! (path: ${CONFIG_FOLDER})`,
          );
        }
        if (!existsSync(CONFIG_FILE)) {
          throw new Error(
            `Configuration file is not exists. (path: ${CONFIG_FILE})`,
          );
        }
        return true;
      }
      private readConfigurationFile(): Configuration | undefined {
        return this.configurationFileExists()
          ? JSON.parse(readFileSync(CONFIG_FILE).toString())
          : undefined;
      }
    }

    export default {};
    ```

  - `index.d.ts`
    ```typescript
    declare type Configuration = {
      port: number;
      host?: string;
    }
    ```