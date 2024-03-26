# Script generated with import_catkin_packages.py.
# For more information: https://github.com/bchretien/arch-ros-stacks.
pkgdesc="ROS - roslaunch is a tool for easily launching multiple ROS nodes locally and remotely via SSH, as well as setting parameters on the Parameter Server."
url='https://wiki.ros.org/roslaunch'

pkgname='ros-noetic-roslaunch'
pkgver='1.16.0'
arch=('any')
pkgrel=2
license=('BSD')

ros_makedepends=(
	ros-noetic-catkin
)

makedepends=(
	'cmake'
	'ros-build-tools'
	${ros_makedepends[@]}
)

ros_depends=(
	ros-noetic-rosout
	ros-noetic-rosparam
	ros-noetic-rosclean
	ros-noetic-rosunit
	ros-noetic-rosgraph-msgs
	ros-noetic-rosmaster
	ros-noetic-roslib
)

depends=(
	${ros_depends[@]}
	python-yaml
	python-paramiko
	python-rospkg
)

_commit="845f74602c7464e08ef5ac6fd9e26c97d0fe42c9"
_dir="ros_comm-${_commit}/tools/roslaunch"
source=("${pkgname}-${pkgver}.tar.gz"::"https://github.com/ros/ros_comm/archive/${_commit}.tar.gz")
sha256sums=('382c8681ac2c9546ef3870d365410ec59ac1bc779cc6c0a68304cf595a66023b')

build() {
	# Use ROS environment variables.
	source /usr/share/ros-build-tools/clear-ros-env.sh
	[ -f /opt/ros/noetic/setup.bash ] && source /opt/ros/noetic/setup.bash

	# Create the build directory.
	[ -d ${srcdir}/build ] || mkdir ${srcdir}/build
	cd ${srcdir}/build

	# Build the project.
	cmake ${srcdir}/${_dir} \
		-DCATKIN_BUILD_BINARY_PACKAGE=ON \
		-DCMAKE_INSTALL_PREFIX=/opt/ros/noetic \
		-DPYTHON_EXECUTABLE=/usr/bin/python \
		-DSETUPTOOLS_DEB_LAYOUT=OFF
	make
}

package() {
	cd "${srcdir}/build"
	make DESTDIR="${pkgdir}/" install
}
