# projecyswordleo
do some changes
<?php
session_start();
include_once 'dbconnect.php';

if(!isset($_SESSION['user']))
{
 header("Location: index.php");
}
$user_id = $_SESSION['user_id'];
$res=mysql_query("SELECT * FROM users WHERE user_id=".$_SESSION['user']);
$userRow=mysql_fetch_array($res);
$query = "SELECT start_date,username,end_date,reason,user_id FROM `leave` WHERE user_id = '1'"; 
$result = mysql_query($query) or die(mysql_error());
$row = mysql_fetch_assoc($result);
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">


<head>
<meta charset="utf-8"/>
<title>Login</title>
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta content="width=device-width, initial-scale=1.0" name="viewport"/>
<meta http-equiv="Content-type" content="text/html; charset=utf-8">
<meta content="" name="description"/>
<meta content="" name="author"/>
<!-- BEGIN GLOBAL MANDATORY STYLES -->
<link href="http://fonts.googleapis.com/css?family=Open+Sans:400,300,600,700&subset=all" rel="stylesheet" type="text/css"/>
<link href="assets/global/plugins/font-awesome/css/font-awesome.min.css" rel="stylesheet" type="text/css"/>
<link href="assets/global/plugins/simple-line-icons/simple-line-icons.min.css" rel="stylesheet" type="text/css"/>
<link href="assets/global/plugins/bootstrap/css/bootstrap.min.css" rel="stylesheet" type="text/css"/>
<link href="assets/global/plugins/uniform/css/uniform.default.css" rel="stylesheet" type="text/css"/>
<!-- END GLOBAL MANDATORY STYLES -->
<!-- BEGIN PAGE LEVEL STYLES -->
<link href="assets/global/plugins/select2/select2.css" rel="stylesheet" type="text/css"/>
<link href="assets/admin/pages/css/login-soft.css" rel="stylesheet" type="text/css"/>
<!-- END PAGE LEVEL SCRIPTS -->
<!-- BEGIN THEME STYLES -->
<link href="assets/global/css/components.css" id="style_components" rel="stylesheet" type="text/css"/>
<link href="assets/global/css/plugins.css" rel="stylesheet" type="text/css"/>
<link href="assets/admin/layout/css/layout.css" rel="stylesheet" type="text/css"/>
<link id="style_color" href="assets/admin/layout/css/themes/default.css" rel="stylesheet" type="text/css"/>
<link href="assets/admin/layout/css/custom.css" rel="stylesheet" type="text/css"/>
<!-- END THEME STYLES -->
<link rel="shortcut icon" href="favicon.ico"/>
</head>
<html>
<body>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Welcome - <?php echo $userRow['username']; ?></title>
<link rel="stylesheet" href="style.css" type="text/css" />
<div id="header">
 <div id="left">
    <label>Swordleo</label>
    </div>
    <div id="right">
     <div id="content">
         Welcome <?php echo $userRow['username']; ?>&nbsp;&nbsp;<a href="logout.php?logout">Sign Out</a>
        </div>
		
    </div>
	</div>
	</br></br></br></br></br></br>
	<div class="portlet-body">
													<a href="#" class="icon-btn">
													<i class="fa fa-group"></i>
													<div>
														 Users
													</div>
													<span class="badge badge-danger">
													<?php echo count($row['username']) ?> </span>
													</a>
												</div>
	<div class="col-md-6">
						<!-- BEGIN BORDERED TABLE PORTLET-->
						<div class="portlet box yellow">
							<div class="portlet-title">
								<div class="caption">
									<i class="fa fa-coffee"></i>Leave Details
								</div>
								<div class="tools">
									<a href="javascript:;" class="collapse">
									</a>
									<a href="#portlet-config" data-toggle="modal" class="config">
									</a>
									<a href="javascript:;" class="reload">
									</a>
									<a href="javascript:;" class="remove">
									</a>
								</div>
							</div>
							<div class="portlet-body">
								<div class="table-scrollable">
									<table class="table table-bordered table-hover">
									<thead>
									<tr>
										<th>
											 User_id
										</th>
										<th>
											 Username
										</th>
										<th>
											 Start_date
										</th>
										<th>
											 End Date
										</th>
										<th>
											 Reason
										</th>
									</tr>
									</thead>
									<tbody>
									<tr>
										<td >
											  <?php echo $row['user_id']; ?>
										</td>
										<td>
											  <?php echo $row['username']; ?>
										</td>
										<td>
											  <?php echo $row['start_date']; ?>
										</td>
										<td>
											  <?php echo $row['end_date']; ?>
										</td>
										<td>
											 <?php echo $row['reason']; ?>
										</td>
									</tr>
									
									</tbody>
									</table>
								</div>
							</div>
						</div>
						<!-- END BORDERED TABLE PORTLET-->
					</div>
				</div>

	<div class="row">
					<div class="col-md-5 col-sm-8">
						<!-- BEGIN SAMPLE TABLE PORTLET-->
						<div class="portlet box red">
							<div class="portlet-title">
								<div class="caption">
									<i class="fa fa-cogs"></i>User Information
								</div>
								
							</div>

		<div class="portlet-body">
								<div class="table-scrollable">
									<table class="table table-hover" border="1">
									<thead>
									<tr>
										<th>
											 User_Id
										</th>
										<th>
											 Username
										</th>
										<th>
											 Age
										</th>
										<th>
											 Gender
										</th>
										
									</tr>
									</thead>
									<tbody>
									<tr>
										<td>
											 <?php echo $userRow['user_id']; ?>
										</td>
										<td>
											 <?php echo $userRow['username']; ?>
										</td>
										<td>
											 <?php echo $userRow['age']; ?>
										</td>
										<td>
											 <?php echo $userRow['gender']; ?>
										</td>
										<td>
										<a type="button" class="btn btn-info btn-md" data-toggle="modal" href="update.php" id="myBtn">Edit</a>
										</td>
										<td>
										<a href="leaves.php" class="btn btn-info" role="button">APPLY FOR A LEAVE</a>
										</td>
									</tr>
                </div>
            </div>
        </div>
	</div>
</div>

</body>
</html>
<script src="assets/global/plugins/jquery.min.js" type="text/javascript"></script>
<script src="assets/global/plugins/jquery-migrate.min.js" type="text/javascript"></script>
<script src="assets/global/plugins/bootstrbootstrap.min.js" type="text/javascript"></script>
<script src="assets/global/plugins/jquery.blockui.min.js" type="text/javascript"></script>
<script src="assets/global/plugins/uniform/jquery.uniform.min.js" type="text/javascript"></script>
<script src="assets/global/plugins/jquery.cokie.min.js" type="text/javascript"></script>
<!-- END CORE PLUGINS -->
<!-- BEGIN PAGE LEVEL PLUGINS -->
<script src="assets/global/plugins/jquery-validatijquery.validate.min.js" type="text/javascript"></script>
<script src="assets/global/plugins/backstretch/jquery.backstretch.min.js" type="text/javascript"></script>
<script type="text/javascript" src="assets/global/plugins/select2/select2.min.js"></script>
<!-- END PAGE LEVEL PLUGINS -->
<!-- BEGIN PAGE LEVEL SCRIPTS -->
<script src="assets/global/scripts/metronic.js" type="text/javascript"></script>
<script src="assets/admin/layout/scripts/layout.js" type="text/javascript"></script>
<script src="assets/admin/layout/scripts/demo.js" type="text/javascript"></script>
<script src="assets/admin/pages/scripts/login-soft.js" type="text/javascript"></script>
<!-- END PAGE LEVEL SCRIPTS -->
<script>
jQuery(document).ready(function() {     
  Metronic.init(); // init metronic core components
Layout.init(); // init current layout
  Login.init();
  Demo.init();
       // init background slide images
       $.backstretch([
        "assets/admin/pages/media/bg/1.jpg",
        "assets/admin/pages/media/bg/2.jpg",
        "assets/admin/pages/media/bg/3.jpg",
        "assets/admin/pages/media/bg/4.jpg"
        ], {
          fade: 1000,
          duration: 8000
    }
    );
});
</script>
</body>
</html>
