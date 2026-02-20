### 系统介绍

基于SpringBoot实现的在线小说阅读平台采用多模块开发的架构方式，前台系统实现了用户注册/登录、首页、全部作品、排行榜、充值、作家专区、我的书架、个人中心等功能模块，后台系统实现了系统登录、首页、基础管理、系统管理、系统监控、研发工具、网站管理、新闻管理、会员管理、作家管理、小说管理、订单管理等功能模块。

### 技术选型

开发工具：idea2020.3+webstorm2020.3

运行环境：jdk17+maven3.6.3+mysql8.0+redis5.0.9

服务端技术：springboot+mybatis+jwt+fastjson

前端技术：html+css+axios+element-ui+echarts

### 成果展示

前台系统->注册/登录
<img width="1896" height="954" alt="前台-登录注册" src="https://github.com/user-attachments/assets/ca78586a-b2df-481a-ad07-ab9d8e9b97e7" />

前台系统->首页
<img width="1875" height="959" alt="前台-首页" src="https://github.com/user-attachments/assets/4d32bc2c-0031-402a-92f6-e2b2d32858f5" />

前台系统->全部作品
<img width="1875" height="1029" alt="前台-全部作品" src="https://github.com/user-attachments/assets/c7cbe6a8-0290-4c8d-b1c5-a3243a2699e7" />

前台系统->排行榜
<img width="1880" height="1034" alt="前台-排行榜" src="https://github.com/user-attachments/assets/62ccc40e-eb1a-4280-a3bf-3be6c3f23c04" />

前台系统->充值
<img width="1874" height="1026" alt="前台-充值" src="https://github.com/user-attachments/assets/c2c91bb1-5696-46ca-a419-9fa1ff4b6946" />

前台系统->作家专区
<img width="1880" height="1028" alt="前台-作家专区" src="https://github.com/user-attachments/assets/91e297ed-7879-48dd-b0cd-48661712cf1a" />

前台系统->我的书架
<img width="1891" height="979" alt="前台-我的书架" src="https://github.com/user-attachments/assets/2e6b1c0b-9086-4529-97fe-f644af551425" />

后台系统->登录
<img width="1909" height="979" alt="后台-登录" src="https://github.com/user-attachments/assets/6d9ea954-b0b9-4969-8758-0e24baa970be" />

后台系统->首页
<img width="1909" height="1000" alt="后台-首页" src="https://github.com/user-attachments/assets/68937d7a-a55b-4e15-8fec-de81968244f3" />

后台系统->基础管理
<img width="1901" height="999" alt="后台-基础管理" src="https://github.com/user-attachments/assets/a0c62c39-7b06-4e7c-81d3-0d6b423fb1db" />

后台系统->系统管理
<img width="1905" height="995" alt="后台-系统管理" src="https://github.com/user-attachments/assets/b32763a7-13ea-4910-bd10-981dc88bc031" />

后台系统->系统监控
<img width="1910" height="996" alt="后台-系统监控" src="https://github.com/user-attachments/assets/fe00866e-bfc5-401c-a50c-5fcb94f6d3ee" />

后台系统->研发工具
<img width="1901" height="988" alt="后台-研发工具" src="https://github.com/user-attachments/assets/4f7f0240-4038-4c59-ab3b-00afc0b725bb" />

后台系统->网站管理
<img width="1899" height="985" alt="后台-网站管理" src="https://github.com/user-attachments/assets/83b82927-6bf9-4f32-bc7d-c6d8bfd4e166" />

后台系统->新闻管理
<img width="1894" height="996" alt="后台-新闻管理" src="https://github.com/user-attachments/assets/8ee0f174-844d-465e-89e1-63aa4c71e3d1" />

后台系统->会员管理
<img width="1900" height="996" alt="后台-会员管理" src="https://github.com/user-attachments/assets/d4d7e5c9-641c-4294-bdb7-044a5b5b3a21" />

后台系统->作家管理
<img width="1899" height="998" alt="后台-作家管理" src="https://github.com/user-attachments/assets/1d75deb1-514d-4d72-9b5b-e98b9a0fea32" />

后台系统->小说管理
<img width="1904" height="995" alt="后台-小说管理" src="https://github.com/user-attachments/assets/0cb13998-57aa-4701-ba94-968cc1e93fa7" />

后台系统->订单管理
<img width="1904" height="996" alt="后台-订单管理" src="https://github.com/user-attachments/assets/afdea346-bfaf-426d-a35c-2890a95813d5" />

### 源码展示

@RequestMapping("book")

@RestController

@Slf4j

@RequiredArgsConstructor

public class BookController extends BaseController {

private final BookService bookService;

private final Map<String, BookContentService> bookContentServiceMap;

//查询首页小说设置列表数据

@GetMapping("listBookSetting")

public RestResult<Map<Byte, List<BookSettingVO>>> listBookSetting() {

    return RestResult.ok(bookService.listBookSettingVO());
    
}

//查询首页点击榜单数据

@GetMapping("listClickRank")

public RestResult<List<Book>> listClickRank() {

    return RestResult.ok(bookService.listClickRank());
    
}

//查询首页新书榜单数据

@GetMapping("listNewRank")

public RestResult<List<Book>> listNewRank() {

    return RestResult.ok(bookService.listNewRank());
    
}

//查询小说分类列表

@GetMapping("listBookCategory")

public RestResult<List<BookCategory>> listBookCategory() {

    return RestResult.ok(bookService.listBookCategory());
    
}

//查询小说详情信息

@GetMapping("queryBookDetail/{id}")

public RestResult<Book> queryBookDetail(@PathVariable("id") Long id) {

    return RestResult.ok(bookService.queryBookDetail(id));
    
}

//查询小说排行信息

@GetMapping("listRank")

public RestResult<List<Book>> listRank(@RequestParam(value = "type", defaultValue = "0") Byte type,
    @RequestParam(value = "limit", defaultValue = "30") Integer limit) {
    
    return RestResult.ok(bookService.listRank(type, limit));
    
}

//查询章节相关信息

@GetMapping("queryBookIndexAbout")

public RestResult<Map<String, Object>> queryBookIndexAbout(Long bookId, Long lastBookIndexId) {

    Map<String, Object> data = new HashMap<>(2);
    data.put("bookIndexCount", bookService.queryIndexCount(bookId));
    BookIndex bookIndex = bookService.queryBookIndex(lastBookIndexId);
    String lastBookContent = bookContentServiceMap.get(bookIndex.getStorageType())
        .queryBookContent(bookId, lastBookIndexId).getContent();
    if (lastBookContent.length() > 42) {
        lastBookContent = lastBookContent.substring(0, 42);
    }
    data.put("lastBookContent", lastBookContent);
    return RestResult.ok(data);
    
}

//根据分类id查询同类推荐书籍

@GetMapping("listRecBookByCatId")

public RestResult<List<Book>> listRecBookByCatId(Integer catId) {

    return RestResult.ok(bookService.listRecBookByCatId(catId));
    
}

//新增评价

@PostMapping("addBookComment")

public RestResult<?> addBookComment(BookComment comment, HttpServletRequest request) {

    UserDetails userDetails = getUserDetails(request);
    if (userDetails == null) {
        return RestResult.fail(ResponseStatus.NO_LOGIN);
    }
    bookService.addBookComment(userDetails.getId(), comment);
    return RestResult.ok();
    
}

}

### 账号地址及其它说明

1、地址说明

前台系统：localhost:8083

后台系统：localhost:8090

2、账号说明

用户：17302210027/123456

管理员：admin/admin

3、目录结构展示

<img width="985" height="169" alt="项目结构" src="https://github.com/user-attachments/assets/07d14948-5876-484b-8425-e7b5be6b51b6" />

4、项目结构展示

<img width="1575" height="763" alt="目录结构" src="https://github.com/user-attachments/assets/50a66652-3769-43c8-b79f-d12b6b9b7ed0" />

5、运行步骤

1）创建数据库、导入sql脚本

2）修改application-dev.yml中的数据库配置文件

3）启动服务端

### 获取方式(可远程调试)

访问链接：https://mbd.pub/o/bread/mbd-YZWXmJ5rZg==

若资源获取失败，可添加happy35596339(vx)或2061772307(qq)进行交流
