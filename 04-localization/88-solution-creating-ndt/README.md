# Solution: Creating NDT

> Part of: **Creating Scan Matching Algorithms**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=YNysnFYR2iQ)

## Summary

**Summary of NDT (Numerical Differentiation Techniques) Lesson**

This lesson covers the implementation of Numerical Differentiation Techniques (NDT) using Python, specifically focusing on creating probability density functions (PDFs) and applying Newton's Method. The lesson provides a step-by-step guide to calculating PDFs, transforming points, and implementing Newton's Method.

**Key Concepts**

* **Probability Density Function (PDF)**: calculated using the equation `e^(-0.5 * x^T * Σ^-1 * x)`, where `x` is the centered vector, `Σ` is the covariance matrix, and `e` is the base of the natural logarithm.
* **Centered Vector**: calculated by subtracting the mean from each input point.
* **Inverse Covariance Matrix (Σ^-1)**: used in calculating the PDF and Newton's Method.
* **Newton's Method**: an iterative method for finding the roots of a function, implemented using partial derivatives and second-order partial derivatives.
* **Partial Derivatives**: calculated as `∂f/∂x` and `∂^2f/∂x^2`, where `f` is the function being optimized.
* **Hessian Matrix (H)**: a square matrix of second-order partial derivatives, used in Newton's Method.

**Practical Notes**

* To calculate the PDF, create a centered vector by subtracting the mean from each input point, then use the equation above to calculate the probability density at each point.
* In implementing Newton's Method, use the partial derivatives and Hessian matrix to iteratively update the estimate of the function's root.
* The lesson provides an example implementation of transforming points using a rotation and translation matrix, which can be used in conjunction with Newton's Method.

Note: This summary is intended as a concise overview of the key concepts and practical steps covered in the lesson. It is not meant to replace the original transcript or provide detailed explanations of each concept.

## Transcript

Let's go ahead and look at the solution for Exercise 3, Lesson 1 for creating NDT. The first part was defining the probability, so that's just using that equation that was listed in the classroom notes of using this e to the power of negative 0.5 times x minus q, this centered vector transpose times that inverse of co-variance times that centered vector, and then just indexing into it correctly that one by one matrix that get a single element that we can take e to the power of. So that's probability. Then we can go ahead and check out the PDF. So these are the matrix calculations for doing that, finding the mean, going through all the different points, adding those together, and then dividing by the total number of points in calculating Sigma.

Very similar, and then going through all those input points, we can see how the calculations are being done here by adding up this centered vector. So centered vector times this center in vector transpose. The point part here is creating this on me, this input point matrix. Now, we can use the create that centered vector, and then dividing everything by the total number of points there, and then that was the main part of doing PDF, and then once we have probability, you can go ahead and visualize that PDF, and then NewtonsMethod, the main part of this exercise, we can see that we grab Q from that cell, that's being input into the function as well as its S, and we can go ahead and inverse that. Since we're using that S inverse most of the time in the calculations, looking, grab this input point here, one point, make a matrix out of it.

Grab calculate the centered vector using that Q in that X, and then all these matrices here are just listed in the classroom, but that's the partial derivatives and second-order partial derivative, and then this E part that shows up a lot in HESI and calculation. So then just going ahead and calculate in G using those equations, and I love the E part, partial derivatives, inverse covariance, that is the Q, center of vector transpose, and then the Hessians, which can involve that second-order partial derivative, and then that will just be added to that, the zero vectors of what was put in for h previous in G previous, and I'll see you at the calculations here. Let's call the partial derivatives and that second-order partial derivative, and so then that's the main part for NewtonsMethod. The rest of the exercise, let me go down to the Main. Was filling in this positive-definite parts, just using five as an increment.

Let's say 0 doesn't work, it's not positive-definite. Increment by 5, try that out and keep going until you get to 100. Might want to try a bigger max value or to say, you can't get to be positive-definite with just that max. Then going ahead and calculating that transform using H and g. Then here, this was doing that transformation.

We calculated T. What do we do with it? Well, we had a point before and we want to transform it when I move it some delta direction based off that transform. You can see this is how it's doing, where two is at theta. We're doing that rotation minus that point y.

Then we also have this two here. We can see that, point x times cosine theta minus point y times sine theta plus 0, 0 is at x minus point x, and make it a vector. Then with that point x times sine theta plus this point y times this cos theta, that's the rotation plus this T of 1 , one was y. Then minus this point y to make it a vector since that was a starting point. Then we have that vector, and then that's changing its magnitude by 0.5 here.

That's how you can do that transformation. That's it for part 1. If we check out part 2, the main things there were also that transformation. That's why we're spinning a little time to take a look at that. Point x times this cosine theta minus point y times a sine theta, that rotation plus x.

That was that transformation there. That's just doing that transformation on our point. Point x times sine theta plus point y times a cos theta plus y, that rotation plus translation. Then this is point.z. In this example, it's all 2D, so that should just be zero.

Okay, so then we did that transformation. We can put that point transformation in the Newton's method and get out that H and g. Now notice that H and g are passed in each time in this. So they keep getting added to for all the points starting at these zeros here. Then this is the same as part 1.

We'll just do this in increments in this max value, calculate the MatrixXd T using H and g. That should be it for completing part 2 of this exercise. Then you can test it by hitting the space and seeing how it converges.

## Additional Content

## Solution: Creating NDT
```
using namespace std;

#include

#include 
#include "helper.h"

using namespace Eigen;
#include 
#include    // TicToc

Pose pose(Point(0,0,0),Rotate(0,0,0));
Pose upose = pose;
bool matching = false;
bool update = false;
void keyboardEventOccurred(const pcl::visualization::KeyboardEvent &event, void* viewer)
{

	if (event.getKeySym() == "Right" && event.keyDown()){
		update = true;
		upose.position.x += 0.1;
  	}
	else if (event.getKeySym() == "Left" && event.keyDown()){
		update = true;
		upose.position.x -= 0.1;
  	}
  	if (event.getKeySym() == "Up" && event.keyDown()){
		update = true;
		upose.position.y += 0.1;
  	}
	else if (event.getKeySym() == "Down" && event.keyDown()){
		update = true;
		upose.position.y -= 0.1;
  	}
	else if (event.getKeySym() == "k" && event.keyDown()){
		update = true;
		upose.rotation.yaw += 0.02;
		while( upose.rotation.yaw > 2*pi)
			upose.rotation.yaw -= 2*pi;  
  	}
	else if (event.getKeySym() == "l" && event.keyDown()){
		update = true;
		upose.rotation.yaw -= 0.02;
		while( upose.rotation.yaw < 0)
			upose.rotation.yaw += 2*pi; 
  	}
	if (event.getKeySym() == "space" && event.keyDown()){
		matching = true;
		
  	}
	else if (event.getKeySym() == "n" && event.keyDown()){
		pose = upose;
		cout << "Set New Pose" << endl;
  	}
	
	
}

double Probability(Eigen::MatrixXd X, Eigen::MatrixXd Q, Eigen::MatrixXd S){
	// TODO: calculate the probibility of the point given mean and standard deviation
	return exp( -0.5 * ( (X-Q).transpose() * S.inverse() * (X-Q) )(0,0) );
}

struct Cell{
	PointCloudT::Ptr cloud;
	Eigen::MatrixXd Q;
	Eigen::MatrixXd S;

	Cell(){
		PointCloudT::Ptr input(new PointCloudT);
		cloud = input;
		Q = Eigen::MatrixXd::Zero(2,1);
		S = Eigen::MatrixXd::Zero(2,2);
	}
};

struct Grid{

	// each cell is a square res x res and total grid size is (2 x width) x (2 x height)
	double res;
	int width;
	int height;

	vector> grid;

	Grid(double setRes, int setWidth, int setHeight){

		res = setRes;
		width = setWidth;
		height = setHeight;

		for(int r = 0; r < height*2; r++ ){
			vector row;
			for(int c = 0; c < width*2; c++){
				row.push_back(Cell());
			}
			grid.push_back(row);
		}
	}

	void addPoint(PointT point){

		//cout << point.x << "," << point.y << endl;

		int c = int((point.x + width * res  ) / res);
		int r = int((point.y + height * res ) / res);

		//cout << r << "," << c << endl;

		if( (c >= 0 && c < width*2) && (r >= 0 && r < height*2) ){
			grid[r][c].cloud->points.push_back(point);
		}
	} 

	void Build(){

		for(int r = 0; r < height*2; r++ ){
			for(int c = 0; c < width*2; c++){

				PointCloudT::Ptr input = grid[r][c].cloud;
				if(input->points.size() > 2){

					// Calculate the mean
					Eigen::MatrixXd Q(2,1);
					Q << Eigen::MatrixXd::Zero(2,1);
					for(PointT point : input->points){
						Q(0,0) += point.x;
						Q(1,0) += point.y;
					}
					Q(0,0) = Q(0,0)/input->points.size();
					Q(1,0) = Q(1,0)/input->points.size();

					grid[r][c].Q = Q;

					// Calculate sigma
					Eigen::MatrixXd S(2,2);
					S << Eigen::MatrixXd::Zero(2,2);
					for(PointT point : input->points){
						Eigen::MatrixXd X(2,1);
						X(0,0) = point.x;
						X(1,0) = point.y;

						S += (X-Q) * (X-Q).transpose();
					}
					S(0,0) = S(0,0)/input->points.size();
					S(0,1) = S(0,1)/input->points.size();
					S(1,0) = S(1,0)/input->points.size();
					S(1,1) = S(1,1)/input->points.size();

					grid[r][c].S = S;
				}
				
			}
		}
	}

	Cell getCell(PointT point){
		int c = int((point.x + width * res  ) / res);
		int r = int((point.y + height * res ) / res);

		if( (c >= 0 && c < width*2) && (r >= 0 && r < height*2) ){
			return grid[r][c];
		}
		return Cell();
	}

	double Value(PointT point){

		Eigen::MatrixXd X(2,1);
		X(0,0) = point.x;
		X(1,0) = point.y;

		double value = 0;
		for(int r = 0; r < height*2; r++ ){
			for(int c = 0; c < width*2; c++){
				if(grid[r][c].cloud->points.size() > 2)
					value += Probability(X, grid[r][c].Q, grid[r][c].S );
			}
		}
		return value;
	}
};

Cell PDF(PointCloudT::Ptr input, int res, pcl::visualization::PCLVisualizer::Ptr& viewer){

	// Calculate the mean
	Eigen::MatrixXd Q(2,1);
	Q << Eigen::MatrixXd::Zero(2,1);
	for(PointT point : input->points){
		Q(0,0) += point.x;
		Q(1,0) += point.y;
	}
	Q(0,0) = Q(0,0)/input->points.size();
	Q(1,0) = Q(1,0)/input->points.size();

	// Calculate sigma
	Eigen::MatrixXd S(2,2);
	S << Eigen::MatrixXd::Zero(2,2);
	for(PointT point : input->points){
		Eigen::MatrixXd X(2,1);
		X(0,0) = point.x;
		X(1,0) = point.y;

		S += (X-Q) * (X-Q).transpose();
	}
	S(0,0) = S(0,0)/input->points.size();
	S(0,1) = S(0,1)/input->points.size();
	S(1,0) = S(1,0)/input->points.size();
	S(1,1) = S(1,1)/input->points.size();

	PointCloudTI::Ptr pdf(new PointCloudTI);
	for(double i = 0.0; i <= 10.0; i += 10.0/double(res)){
		for(double j = 0.0; j <= 10.0; j += 10.0/double(res)){
			Eigen::MatrixXd X(2,1);
			X(0,0) = i;
			X(1,0) = j;

			PointTI point;
			point.x = i;
			point.y = j;
			point.z = Probability(X,Q,S);
			point.intensity = point.z;
			pdf->points.push_back(point);
		}
	}
	renderPointCloudI(viewer, pdf, "pdf");

	Cell cell = Cell();
	cell.S = S;
	cell.Q = Q;
	cell.cloud = input;
	return cell;
}

template
void NewtonsMethod(PointT point, double theta, Cell cell, Eigen::MatrixBase& g_previous, Eigen:: MatrixBase& H_previous){

	Eigen::MatrixXd Q = cell.Q;
	Eigen::MatrixXd Si = cell.S.inverse();

	Eigen::MatrixXd X(2,1);
	X(0,0) = point.x;
	X(1,0) = point.y;

	Eigen::MatrixXd q = X - Q;

	Eigen::MatrixXd q_p1(2,1);
	q_p1(0,0) = 1.0;
	q_p1(1,0) = 0.0;
	Eigen::MatrixXd q_p2(2,1);
	q_p2(0,0) = 0.0;
	q_p2(1,0) = 1.0;
	Eigen::MatrixXd q_p3(2,1);
	q_p3(0,0) = -point.x*sin(theta)-point.y*cos(theta);
	q_p3(1,0) =  point.x*cos(theta)-point.y*sin(theta);

	Eigen::MatrixXd q_pp(2,1);
	q_pp(0,0) = -point.x*cos(theta)+point.y*sin(theta);
	q_pp(1,0) = -point.x*sin(theta)-point.y*cos(theta);

	Eigen::MatrixXd EXP(1,1);
	EXP(0,0) = exp(-0.5 * (q.transpose() * Si * q)(0,0) );

	Eigen::MatrixXd g(3,1);
	g(0,0) = (q.transpose() * Si * q_p1 * EXP)(0,0);
	g(1,0) = (q.transpose() * Si * q_p2 * EXP)(0,0);
	g(2,0) = (q.transpose() * Si * q_p3 * EXP)(0,0);

	Eigen::MatrixXd H(3,3);
	H(0,0) = (-EXP*( (-q.transpose()*Si*q_p1)*(-q.transpose()*Si*q_p1)+(-q_p1.transpose()*Si*q_p1)))(0,0);
	H(0,1) = (-EXP*( (-q.transpose()*Si*q_p1)*(-q.transpose()*Si*q_p2)+(-q_p2.transpose()*Si*q_p1)))(0,0);
	H(0,2) = (-EXP*( (-q.transpose()*Si*q_p1)*(-q.transpose()*Si*q_p3)+(-q_p3.transpose()*Si*q_p1)))(0,0);
	H(1,0) = (-EXP*( (-q.transpose()*Si*q_p2)*(-q.transpose()*Si*q_p1)+(-q_p1.transpose()*Si*q_p2)))(0,0);
	H(1,1) = (-EXP*( (-q.transpose()*Si*q_p2)*(-q.transpose()*Si*q_p2)+(-q_p2.transpose()*Si*q_p2)))(0,0);
	H(1,2) = (-EXP*( (-q.transpose()*Si*q_p2)*(-q.transpose()*Si*q_p3)+(-q_p3.transpose()*Si*q_p2)))(0,0);
	H(2,0) = (-EXP*( (-q.transpose()*Si*q_p3)*(-q.transpose()*Si*q_p1)+(-q_p1.transpose()*Si*q_p3)))(0,0);
	H(2,1) = (-EXP*( (-q.transpose()*Si*q_p3)*(-q.transpose()*Si*q_p2)+(-q_p2.transpose()*Si*q_p3)))(0,0);
	H(2,2) = (-EXP*( (-q.transpose()*Si*q_p3)*(-q.transpose()*Si*q_p3)+(-q.transpose()*Si*q_pp)+(-q_p3.transpose()*Si*q_p3)))(0,0);

	H_previous += H;
	g_previous += g;

}
double Score(PointCloudT::Ptr cloud, Grid grid){
	double score = 0;
	for(PointT point:cloud->points){
		Cell cell = grid.getCell(point);
		if(cell.cloud->points.size() > 2){
			score += grid.Value(point);
		}
	}
	return score;
}

double AdjustmentScore(double alpha, Eigen::MatrixXd T, PointCloudT::Ptr source, Pose pose, Grid grid){

	T *= alpha;
	pose.position.x += T(0,0);
	pose.position.y += T(1,0);
	pose.rotation.yaw += T(2,0);
	while(pose.rotation.yaw > 2*pi)
		pose.rotation.yaw -= 2*pi;

	
	Eigen::Matrix4d transform = transform3D(pose.rotation.yaw, 0, 0, pose.position.x, pose.position.y, 0);

	PointCloudT::Ptr transformed_scan (new PointCloudT);
	pcl::transformPointCloud (*source, *transformed_scan, transform);

	double score = Score(transformed_scan, grid);

	//cout << "score would be " << score << endl;

	return score;

}

double computeStepLength(Eigen::MatrixXd T, PointCloudT::Ptr source, Pose pose, Grid grid, double currScore){
	double maxParam = max( max( T(0,0), T(1,0)), T(2,0) );
	double mlength = 1.0;
	if(maxParam > 0.2){
		mlength =  0.1/maxParam;
		T *= mlength;
	}

	double bestAlpha = 0;

	//Try smaller steps
	double alpha = 1.0;
	for(int i = 0; i < 40; i++){
		//cout << "Adjusting alpha smaller" << endl;
		double adjScore = AdjustmentScore(alpha, T, source, pose, grid);
		if( adjScore > currScore){
			bestAlpha = alpha;
			currScore = adjScore;
		}
		alpha *= .7;
	}
	if(bestAlpha == 0){
		//Try larger steps
		alpha = 2.0;
		for(int i = 0; i < 10; i++){
			//cout << "Adjusting alpha bigger" << endl;
			double adjScore = AdjustmentScore(alpha, T, source, pose, grid);
			if( adjScore > currScore){
				bestAlpha = alpha;
				currScore = adjScore;
			}
			alpha *= 2;
		}
	}

	return bestAlpha * mlength;
}

template
double PosDef(Eigen::MatrixBase& A, double start, double increment, int maxIt){

	bool pass = false;
	int count = 0;

	A += start * Eigen::Matrix3d::Identity ();
	
	while(!pass && count < maxIt){

		Eigen::LLT lltOfA(A); // compute the Cholesky decomposition of A

    	if(lltOfA.info() == Eigen::NumericalIssue){
			A += increment * Eigen::Matrix3d::Identity ();
			count++;
    	}
		else{
			pass = true;
		}
	}

	return  start + increment * count;
}
```
```
int main(){

	pcl::visualization::PCLVisualizer::Ptr viewer (new pcl::visualization::PCLVisualizer ("NDT Creation"));
  	viewer->setBackgroundColor (0, 0, 0);
  	viewer->addCoordinateSystem (1.0);
	viewer->registerKeyboardCallback(keyboardEventOccurred, (void*)&viewer);

	// Part 1: Visualize a PDF cell
	bool part1 = false;
	if(part1){
		// Create Input from set of points in (x,y) range 0 - 10
		PointCloudT::Ptr input(new PointCloudT);
  		input->points.push_back(PointT(4, 4, 0));
		input->points.push_back(PointT(4, 9, 0));
		input->points.push_back(PointT(5, 5, 0));
		input->points.push_back(PointT(5, 2, 0));
		input->points.push_back(PointT(7, 5, 0));
		
		// render cell border
		renderRay(viewer, PointT(0,0,0), PointT(0,10,0), "left", Color(0,0,1));
		renderRay(viewer, PointT(0,10,0), PointT(10,10,0), "top", Color(0,0,1));
		renderRay(viewer, PointT(10,10,0), PointT(10,0,0), "right", Color(0,0,1));
		renderRay(viewer, PointT(0,0,0), PointT(10,0,0), "bottom", Color(0,0,1));

		// TODO: finish writing the PDF function to visualize the 2D gaussian
		Cell cell = PDF(input, 200, viewer);

		// Test points
		PointT point(1,2,1); // CANDO: change test point to see how it converges
		
		input->points.push_back(PointT(point.x, point.y, 1.0));
		for(int iteration = 0; iteration < 20; iteration++){ // TODO: increase the iteration count to get convergence
			
			Eigen::MatrixXd g(3,1);
			g << Eigen::MatrixXd::Zero(3,1);

			Eigen::MatrixXd H(3,3);
			H << Eigen::MatrixXd::Zero(3,3);

			// TODO: finish writing the NewtonsMethod function
			NewtonsMethod(point, 0, cell, g, H);
			PosDef(H, 0, 5, 100); // TODO: change the increment and max values to nonzero values
			// TODO: calculate the 3 x 1 matrix T by using H inverse and g
			Eigen::MatrixXd T = -H.inverse()*g;

			// TODO: calculate the new point by transforming point by the T matrix which is [x translation, y translation, theta rotation]
			// 	   pointT(new x, new y, 1), values below should be nonzero
			PointT pointT(point.x * cos(T(2,0)) - point.y * sin(T(2,0)) + T(0,0) - point.x ,  point.x * sin(T(2,0)) + point.y * cos(T(2,0)) + T(1,0) - point.y , 1);
			double magT = sqrt(pointT.x*pointT.x + pointT.y*pointT.y);
			double maxDelta = 0.5; // CANDO: change the step size value
			pointT.x *= maxDelta/magT;
			pointT.y *= maxDelta/magT;
			PointT point2(point.x+pointT.x, point.y+pointT.y,1);

			renderRay(viewer, point, point2, "gradient_"+to_string(iteration), Color(1,1,1));
			input->points.push_back(PointT(point2.x, point2.y, 1.0));
			point = point2;
		}

		renderPointCloud(viewer, input, "input", Color(0,0,1));

		while (!viewer->wasStopped ())
  		{
  			viewer->spinOnce ();
  		}
	}

	// Part 2: Multiple PDF cells for target
	else{
		// Load target
		PointCloudT::Ptr target(new PointCloudT);
  		pcl::io::loadPCDFile("target.pcd", *target);
	
		renderPointCloud(viewer, target, "target", Color(0,0,1));
		
		Grid ndtGrid(3.0, 2, 2); //CANDO: change grid dimension parameters
		
		for(PointT point : target->points){
			ndtGrid.addPoint(point);
		}
		ndtGrid.Build();
		
		// Draw grid
		int rowc = 0;
		for(double y = -ndtGrid.height * ndtGrid.res; y <= ndtGrid.height * ndtGrid.res; y += ndtGrid.res){
			renderRay(viewer, PointT(-ndtGrid.width * ndtGrid.res,y,0), PointT(ndtGrid.width * ndtGrid.res,y,0), "grid_row_"+to_string(rowc), Color(0,0,1));
			rowc++;
		}
		int colc = 0;
		for(double x = -ndtGrid.width * ndtGrid.res; x <= ndtGrid.width * ndtGrid.res; x += ndtGrid.res){
			renderRay(viewer, PointT(x,-ndtGrid.height * ndtGrid.res,0), PointT(x,ndtGrid.height * ndtGrid.res,0), "grid_col_"+to_string(colc), Color(0,0,1));
			colc++;
		}
	
		// Draw total PDF from all cells
		
		PointCloudTI::Ptr pdf(new PointCloudTI);
		int res = 10;
		for(double y = -ndtGrid.height * ndtGrid.res; y <= ndtGrid.height * ndtGrid.res; y += ndtGrid.res/double(res)){
			for(double x = -ndtGrid.width * ndtGrid.res; x <= ndtGrid.width * ndtGrid.res; x += ndtGrid.res/double(res)){
				Eigen::MatrixXd X(2,1);
				X(0,0) = x;
				X(1,0) = y;
	
				PointTI point;
				point.x = x;
				point.y = y;
				double value = ndtGrid.Value(PointT(x,y,0));
				point.z = value;
				point.intensity = value;
				if(value > 0.01)
					pdf->points.push_back(point);
			}
		}
		
		renderPointCloudI(viewer, pdf, "pdf");
	
		// Load source
		PointCloudT::Ptr source(new PointCloudT);
  		pcl::io::loadPCDFile("source.pcd", *source);
	
		renderPointCloud(viewer, source, "source", Color(1,0,0));
	
		double sourceScore = Score(source, ndtGrid);
		
		viewer->addText("Score: "+to_string(sourceScore), 200, 200, 32, 1.0, 1.0, 1.0, "score",0);
	
		double currentScore = sourceScore;
	
		int iteration = 0;
  		while (!viewer->wasStopped ())
  		{
	
			if(matching){
	
				viewer->removeShape("score");
				viewer->addText("Score: "+to_string(currentScore), 200, 200, 32, 1.0, 1.0, 1.0, "score",0);
	
				Eigen::MatrixXd g(3,1);
				g << Eigen::MatrixXd::Zero(3,1);
	
				Eigen::MatrixXd H(3,3);
				H << Eigen::MatrixXd::Zero(3,3);
	
				for(PointT point:source->points){
					Cell cell = ndtGrid.getCell(point);
					if(cell.cloud->points.size() > 2){
						double theta = pose.rotation.yaw;
						double x = pose.position.x;
						double y = pose.position.y;
	
						// TODO: calculate the new point pointTran, by transforming point by x, y, and theta 
						// 	   pointTran(new x, new y, point.z), values below should be nonzero
						PointT pointTran(point.x*cos(theta)-point.y*sin(theta)+x, point.x*sin(theta)+point.y*cos(theta)+y, point.z);
						NewtonsMethod(pointTran, theta, cell, g, H);
					}
				}
				
				PosDef(H, 0, 5, 100); // TODO: change the increment and max values to nonzero values
	
				Eigen::MatrixXd T = -H.inverse()*g;
	
				double alpha = computeStepLength(T, source, pose, ndtGrid, currentScore); // CANDO: tweek the computeStepLength function, not optimized
	
				T *= alpha;
	
				pose.position.x += T(0,0);
				pose.position.y += T(1,0);
				pose.rotation.yaw += T(2,0);
				while(pose.rotation.yaw > 2*pi)
					pose.rotation.yaw -= 2*pi;
	
				Eigen::Matrix4d transform = transform3D(pose.rotation.yaw, 0, 0, pose.position.x, pose.position.y, 0);
	
				PointCloudT::Ptr transformed_scan (new PointCloudT);
				pcl::transformPointCloud (*source, *transformed_scan, transform);
	
				double ndtScore = Score(transformed_scan, ndtGrid);
				
				viewer->removeShape("nscore");
				viewer->addText("NDT Score: "+to_string(ndtScore), 200, 150, 32, 1.0, 1.0, 1.0, "nscore",0);
				currentScore = ndtScore;
				iteration++;
	
				viewer->removePointCloud("ndt_scan");
				renderPointCloud(viewer, transformed_scan, "ndt_scan", Color(0,1,0));
	
				matching = false;
			}
			else if(update){
	
				Eigen::Matrix4d userTransform = transform3D(upose.rotation.yaw, upose.rotation.pitch, upose.rotation.roll, upose.position.x, upose.position.y, upose.position.z);
	
				PointCloudT::Ptr transformed_scan (new PointCloudT);
  				pcl::transformPointCloud (*source, *transformed_scan, userTransform);
				viewer->removePointCloud("usource");
				renderPointCloud(viewer, transformed_scan, "usource", Color(0,1,1));
	
				
				double score = Score(transformed_scan, ndtGrid);
				viewer->removeShape("score");
				viewer->addText("Score: "+to_string(score), 200, 200, 32, 1.0, 1.0, 1.0, "score",0);
				
				update = false;
				
			}
			
  			viewer->spinOnce ();
  		}
  	}
  	
	return 0;
}
```
