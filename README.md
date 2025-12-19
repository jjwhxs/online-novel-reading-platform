### 系统介绍

基于SpringBoot实现的在线小说阅读平台采用多模块开发的架构方式，前台系统实现了用户注册/登录、首页、全部作品、排行榜、充值、作家专区、我的书架、个人中心等功能模块，后台系统实现了系统登录、首页、基础管理、系统管理、系统监控、研发工具、网站管理、新闻管理、会员管理、作家管理、小说管理、订单管理等功能模块。

### 技术选型

开发工具：idea2020.3+webstorm2020.3

运行环境：jdk17+maven3.6.3+mysql8.0+redis5.0.9

服务端技术：springboot+mybatis+jwt+fastjson

前端技术：html+css+axios+element-ui+echarts

### 成果展示

前台系统->注册/登录 输入图片说明

前台系统->首页 输入图片说明

前台系统->全部作品 输入图片说明

前台系统->排行榜 输入图片说明

前台系统->充值 输入图片说明

前台系统->作家专区 输入图片说明

前台系统->我的书架 输入图片说明

后台系统->登录 输入图片说明

后台系统->首页 输入图片说明

后台系统->基础管理 输入图片说明

后台系统->系统管理 输入图片说明

后台系统->系统监控 输入图片说明

后台系统->研发工具 输入图片说明

后台系统->网站管理 输入图片说明

后台系统->新闻管理 输入图片说明

后台系统->会员管理 输入图片说明

后台系统->作家管理 输入图片说明

后台系统->小说管理 输入图片说明

后台系统->订单管理 输入图片说明

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

输入图片说明

4、项目结构展示

输入图片说明

5、运行步骤

1）创建数据库、导入sql脚本

2）修改application-dev.yml中的数据库配置文件

3）启动服务端

### 获取方式(可远程调试)

访问链接(在浏览器中手动输入下图中的地址)： 输入图片说明

若资源获取失败，可添加happy35596339(vx)或1204901965(qq)进行交流
